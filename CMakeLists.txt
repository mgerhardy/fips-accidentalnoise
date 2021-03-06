fips_begin_lib(accidentalnoise)
	include_directories(accidental-noise-library/Imaging accidental-noise-library/Noise accidental-noise-library/RGBA accidental-noise-library/Volume)
	fips_files(
		accidental-noise-library/RGBA/rgbacolorops.cpp
		accidental-noise-library/RGBA/rgbaselect.cpp
		accidental-noise-library/RGBA/rgbacurve.cpp
		accidental-noise-library/RGBA/rgbablendops.cpp
		accidental-noise-library/RGBA/rgbahsvtorgba.cpp
		accidental-noise-library/RGBA/rgbablend.cpp
		accidental-noise-library/RGBA/rgbaconstant.cpp
		accidental-noise-library/RGBA/rgbaimplicitgrayscale.cpp
		accidental-noise-library/RGBA/rgbarotatecolor.cpp
		accidental-noise-library/RGBA/rgbacomposechannels.cpp
		accidental-noise-library/RGBA/rgbanormalize.cpp
		accidental-noise-library/RGBA/rgbargbatohsv.cpp
		accidental-noise-library/RGBA/hsv.cpp
		accidental-noise-library/Builder/treecontainer.cpp
		accidental-noise-library/Imaging/implicitbufferbumpmap.cpp
		accidental-noise-library/Imaging/implicitbuffersimpleerode.cpp
		accidental-noise-library/Imaging/rgbabufferrgbaadapter.cpp
		accidental-noise-library/Imaging/mapping.cpp
		accidental-noise-library/Imaging/implicitbufferblur.cpp
		accidental-noise-library/Imaging/rgbabufferblur.cpp
		accidental-noise-library/Imaging/erosion.cpp
		accidental-noise-library/Imaging/implicitbufferfile.cpp
		accidental-noise-library/Imaging/arrayoperations.cpp
		accidental-noise-library/Imaging/rgbabuffernormalmap.cpp
		accidental-noise-library/Imaging/implicitbufferconstant.cpp
		accidental-noise-library/Imaging/rgbabufferimplicitbufferadapter.cpp
		accidental-noise-library/Imaging/implicitbufferselect.cpp
		accidental-noise-library/Imaging/rasterization.cpp
		accidental-noise-library/Imaging/implicitbufferunarymath.cpp
		accidental-noise-library/Imaging/implicitbufferimplicitadapter.cpp
		accidental-noise-library/Imaging/rgbabufferimplicitbuffermultiply.cpp
		accidental-noise-library/Imaging/implicitbufferbase.cpp
		accidental-noise-library/Imaging/rgbabufferselect.cpp
		accidental-noise-library/Imaging/implicitbufferscaletorange.cpp
		accidental-noise-library/Imaging/stb_image.c
		accidental-noise-library/Imaging/stb_image_write.c
		accidental-noise-library/Noise/implicitcurve.cpp
		accidental-noise-library/Noise/implicitcache.cpp
		accidental-noise-library/Noise/implicitblend.cpp
		accidental-noise-library/Noise/implicitmath.cpp
		accidental-noise-library/Noise/implicitsphere.cpp
		accidental-noise-library/Noise/implicitextractrgbachannel.cpp
		accidental-noise-library/Noise/implicitnormalizecoords.cpp
		accidental-noise-library/Noise/implicitfractal.cpp
		accidental-noise-library/Noise/implicitsawtooth.cpp
		accidental-noise-library/Noise/implicitfunctiongradient.cpp
		accidental-noise-library/Noise/implicitcombiner.cpp
		accidental-noise-library/Noise/implicitscaledomain.cpp
		accidental-noise-library/Noise/implicitmagnitude.cpp
		accidental-noise-library/Noise/implicittiers.cpp
		accidental-noise-library/Noise/implicittriangle.cpp
		accidental-noise-library/Noise/implicitgradient.cpp
		accidental-noise-library/Noise/implicitscaleoffset.cpp
		accidental-noise-library/Noise/implicitmodulebase.cpp
		accidental-noise-library/Noise/implicitclamp.cpp
		accidental-noise-library/Noise/implicitconstant.cpp
		accidental-noise-library/Noise/implicitseamlessmapping.cpp
		accidental-noise-library/Noise/implicitcellular.cpp
		accidental-noise-library/Noise/implicitbrightcontrast.cpp
		accidental-noise-library/Noise/implicitbasisfunction.cpp
		accidental-noise-library/Noise/implicitrotatedomain.cpp
		accidental-noise-library/Noise/implicittranslatedomain.cpp
		accidental-noise-library/Noise/noise_lut.cpp
		accidental-noise-library/Noise/cellulargen.cpp
		accidental-noise-library/Noise/noise_gen.cpp
		accidental-noise-library/Noise/implicitselect.cpp
		accidental-noise-library/Noise/implicitautocorrect.cpp
		accidental-noise-library/Noise/implicitrgbadotproduct.cpp
	)
	# hack to silence some warnings
	if (FIPS_MACOS)
		add_definitions(-Wno-sign-compare -Wno-reorder -Wno-deprecated-declarations)
	elseif(FIPS_LINUX)
		add_definitions(-Wno-sign-compare -Wno-reorder)
	endif()
fips_end_lib()

if (FIPS_GCC)
	set_target_properties(accidentalnoise PROPERTIES COMPILE_FLAGS "-O2")
elseif (FIPS_CLANG)
	set_target_properties(accidentalnoise PROPERTIES COMPILE_FLAGS "-O2")
elseif (FIPS_MSVC)
	set_target_properties(accidentalnoise PROPERTIES COMPILE_FLAGS "/Ox")
endif()
