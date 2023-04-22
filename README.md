# Fraunhofer-Lines
## Aim
To study the spectrum of the sun using a spectroscope and computational tools, and determine the
temperature of the sun using the data.

## Theory
### Thermal Radiation
Thermal radiation is the process of converting thermal energy into electromagnetic energy. This
occurs when the atoms and molecules in an object, which are arranged in a lattice structure, collide
with each other, resulting in acceleration and deceleration and the emission of electromagnetic
radiation. The more erratic the jiggling of the atoms and molecules, the higher the temperature
and the more frequent the collisions, leading to a continuous spectrum of light. It is interesting to
note that objects at the same temperature emit the same spectrum of light, with identical intensities
across different wavelengths.

### Black Body Radiation and Wien’s Displacement Law
A black body is an idealised object that absorbs all electromagnetic radiation, emitting it as black
body radiation (essentially electromagnetic radiation) when at thermal equilibrium. At room temperature, it appears black as most of the energy it emits is in the invisible infrared range. As its temperature increases, its colour changes from dull red to bluish white, with the peak wavelength of its spectrum moving towards the blue end of the spectrum. The black body spectrum was experimentally known, but classical physics could not accurately explain its form. Therefore, Max Planck introduced a formula that explained that energy was absorbed or emitted in discrete energy packets or quanta –

$E = hν$ (1)

Here, h is the Planck’s constant ($6.626 \text{ × } 10^{−34}$). The black body spectrum can determine temperature but not composition, and the temperature can be found using Wien’s Displacement Law,

$λ_{\text{peak}} = b/T$ (2)

where b is Wein’s displacement constant ($2.89777 \text{ × } 10^{−3}$ m/K). This constant relates the wavelength of the peak to the temperature of the black body. An interesting fact to note is that the CMB (Cosmic Microwave Background) radiation temperature is a measure of the average energy of the
photons that make up the radiation, which is why it is commonly said that the CMB radiation has
a temperature of 2.73 K.

### Fraunhofer Lines
Fraunhofer lines are a set of dark lines observed in the spectrum of the sun or other stars. This is caused by the absorption of specific wavelengths of light by elements in the outer layers of the sun’s atmosphere. Each element absorbs light at specific wavelengths, and this results in a pattern of dark lines in the spectrum of the star. These lines can be used to identify the elements present in the star’s atmosphere and how relatively abundant they are. By analysing the spectrum of a star, astronomers can gain insights into its composition and temperature. The study of Fraunhofer lines is a very useful tool in astronomy, and has played a critical role in the understanding of our universe.

### Apparatus
1. A spectroscope with a slit, and a diffraction grating
2. A piece of black cloth to cover the spectroscope with while taking pictures
3. A DSLR camera to record the spectrum.
4. A tripod stand for the DSLR camera
5. A retort stand to clasp the spectroscope

### Experimental Set-up
The given spectroscope must first be clamped onto the retort stand and adjusted to a suitable height. Once this is done, the legs of the tripod stand for the DSLR should be spread out as much as possible and tightened, after which a DSLR camera can be mounted onto it. Adjust the height of the DSLR such that a clear and complete spectrum is visible through it. The camera could also be tilted vertically to obtain the spectrum through the camera. It should be noted that while the spectrum is being photographed, the gap between the spectroscope and the camera must be covered using the given black cloth to avoid stray light from interfering with the images.

### Procedure
After setting up the apparatus required for experiment, the spectroscope pointed at the blue sky as it was a clear day. Then, photos of the spectrum were taken such that we could see as many dark lines as possible. While capturing the images, the conditions required for a clear image were tested, and it was found that a very narrow slit aperture for the spectroscope and a low ISO and high shutter speed for the DSLR resulted in non-grainy images with many absorption lines. We had shot as many images as we could and chose the best one for analysis. One thing we noticed was that as we reduced the aperture of the slit, numerous horizontal lines were visible, and this was due to the imperfections in the slits of the diffraction grating inside the spectroscope.

#### Precautions
1. Ensure that the photo is not overexposed as overexposed photos will not show variation in intensity with wavelength. This can be done by adjusting the slit width.
2. When analysing the image, the lines must vertically aligned so that the averaging makes sense.

#### Analysis and Calculations
The analysis of the spectrum was done using Python on Google Colaboratory. First, the image was loaded onto the IDE using the imread function of the matplotlib.pyplot package. This function returns a multidimensional array that contains the image data. For a JPG file, the returned array has three dimensions – (M, N, 3), where M is the number of verical pixels, N is the number of horizontal pixels and 3 refers to the colour channels (red, green and blue). After this, the image data was separated into red, green and blue channels (which are of the form of NumPy arrays) in order to be converted to greyscale. To get a grey channel, we used the following equation –

grey $= 0.2126 · R + 0.7152 · G + 0.0722 · B$ (3)

where R, G, and B are arrays of dimension (M, N), and the resultant array grey is a weighted average of the three channels (with the same dimension). After this, we proceeded to compute the intensity profile of the spectrum. To do this, a random pixel was first taken for which a one-dimensional array of N elements was obtained. Then, the elements of the array were plotted as a function of the pixel number N. This process was continued for multiple pixels and it was observed that the trend was the same for all the pixels. The dips in the graphs represent the dark lines in the absorption spectrum.

Then, the average curve was then plotted and two particular dips were chosen to map the pixel position to a corresponding wavelength. We had chosen the $D_1 + D_2$ sodium doublet wavelength (about 589.29 nm) and the $F$ wavelength (486.134 nm), which are two prominent Fraunhofer lines of the sun as seen in the graph.

As a diffraction grating is being used in the spectroscope to split the light and produce a spectrum, one can use the fact that if a specific wavelength strikes the grating, it forms a symmetric pattern of maxima around a central maximum. The position of these bright fringes is given by the relation –

$d sin θλ = nλ$ for $n = 1, 2, 3,~...$ (4)

Here, $n$ (the order) is 1, and assuming that $θλ << 1$, it could be said that $sin θ ≈ θ ≈ p/D$, where $p$ is the pixel position and $D$ is the perpendicular distance from the central maximum from the DSLR. Using this and two known wavelengths and their corresponding pixels ($D_1 + D_2$ and $F$), we found the constants $K_1$ and $K_2$, where $K_1$ is nanometers per pixel, and the constant $K_2$ is merely a constant offset from the slit. They are related through the following equation –

$λ = K_{1}p + K_{2}$ (5)

This can be obtained from the fact that $λ ∝ p$. Using this, the wavelengths of other dips in the spectrum were plotted. After mapping the position of the pixels to the wavelength, the wavelength with the maximum intensity was found using the graph and applying Wien’s displacement law, the temperature of the Sun was calculated.
