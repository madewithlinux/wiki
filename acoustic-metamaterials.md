# acoustic metamaterials
tags:
  [[geometry]]
  [[3d-printing]]
- [acoustic metamaterials](#acoustic-metamaterials)
- [background/motivation](#backgroundmotivation)
- [theory (as I understand it)](#theory-as-i-understand-it)
  - [half-wavelength pipes](#half-wavelength-pipes)
  - [resonators](#resonators)
  - [pockets](#pockets)
- [my attempts at 3d printing acoustic metamaterials](#my-attempts-at-3d-printing-acoustic-metamaterials)
- [further reading](#further-reading)


# background/motivation
Acoustic metamaterials are like optical lenses, but for sound.
But also more different than that:
* optical lenses work using two materials with different optical properties. (usually one of those materials is air)
* metamaterials (including acoustic metamaterials) work using physical structures that are much smaller than the wavelength you're interested in

Acoustic metamaterials can do various things, like reflect sound, block sound, amplify sound (I think?), but I am pretty much only interested in blocking sound, because I like peace and quiet. So the rest of this page is written assuming that's all that acoustic metamaterials are for.


# theory (as I understand it)
I have seen roughly three types of acoustic metamaterials: pockets, resonators, and half-wavelength pipes.

## half-wavelength pipes
From the paper "Ultra-open acoustic metamaterial silencer based on Fano-like interference", among others.

I think this design can only be used to make a notch filter? (to block a specific frequency of sound)
The basic idea is that the sound has two paths through the material, and the difference between the two paths is half of the wavelength of the sound that you want to block. Thus, destructive interference happens.

pro:
* open to airflow (so it could potentially block noise from a fan)

two issues with this approach:
* it's only good at blocking the one specific frequency that it is 'tuned' to
  * fan noise isn't typically single-frequency, it's more of a mountain centered on some frequency. (at least, most of my noisy fans seem to be like this)
* for low frequencies, half-wavelength is actually relatively long
* I think the actual airflow across the material would affect this in some way? The paper doesn't discuss this (that I saw), and their test setup uses a subwoofer, not a fan.
  * That's not a knock against the paper, though. A subwoofer is a much more replicable noise source than a fan


## resonators
"A lightweight vibro-acoustic metamaterial demonstrator: Numerical and experimental investigation" discusses a design of this type.

I think the idea is that it is anti-resonant at the frequencies that you want to block.

pro:
* seems like it could block sound much better?
* probably works well for low frequencies

con:
* the math seems to be much harder (I do not understand it)
* probably a design that uses this would be closed-off, and permit no airflow


## pockets
Such as in "3D Single-port Labyrinthine Acoustic Metamaterial" and "Broadband fractal acoustic metamaterials for low-frequency sound attenuation"

Seems to be a similar concept to the half-wavelength pipes, but this time the pipes have only one end open. So they're like long, deep holes, or channels, or something. (It's got to be much longer than it is wide, because the width must be much smaller than the sound wavelength in order for it to function as a metamaterial)

mostly the sam pros/cons as the half-wavelength pipes concept, except this design is generally non-ventilated, so you don't have to worry about airflow I guess.


# my attempts at 3d printing acoustic metamaterials
[OnShape cad link](https://cad.onshape.com/documents/11e88f7f2a82f41a2e47ee38/w/92d0c560f7119a5b298fa058/e/bf6c001f1ead5103454eb14e)

Motivation: I've got some 24V fans that I run at 5V in some projects, for very quiet ventilation. But they still make a little bit of noise, around 400Hz and 8-10kHz. 
[here's a spectrum graph of the noise](images/2020-09-06-11-35-27.png)

So, of course, I want to block this noise. I based my approach on the design presented in "Ultra-open acoustic metamaterial silencer based on Fano-like interference". I made some designs that looked quite impressive, but nothing really worked.

probable problems:
* maybe my acoustic filter was too close to the fan?
* maybe my 3D print was not accurate enough, or the surface was too rough
  * also, maybe my half-wavelength pipes themselves were too small? or too big?
* I wasn't really sure if it was the 400Hz or the 10kHz noise that was most annoying to me.
  I started out thinking it was the 400Hz, but later I realized that it's probably the 10kHz because human ears (and mine especially) are more sensitive to high frequencies.
* most of all: I think the noise peak around 8-10kHz was too wide to be effectively blocked by this design.




# further reading
AKA link dump of various papers and other reference material that I have found
* [Ultra-open acoustic metamaterial silencer based on Fano-like interference](https://journals.aps.org/prb/abstract/10.1103/PhysRevB.99.024302)
* [A lightweight vibro-acoustic metamaterial demonstrator: Numerical and experimental investigation - ScienceDirectScienceDirect](https://www.sciencedirect.com/science/article/abs/pii/S088832701500391X)
* [Broadband fractal acoustic metamaterials for low-frequency sound attenuation](https://aip.scitation.org/doi/10.1063/1.4963347)
* [Noise & Vibration Research Group – Mecha(tro)nic System Dynamics](https://www.mech.kuleuven.be/en/mod)
* [A lightweight vibro-acoustic metamaterial demonstrator: Numerical and experimental investigation - ScienceDirect](https://www.sciencedirect.com/science/article/abs/pii/S088832701500391X)
* [Ultra-open ventilated metamaterial absorbers for sound-silencing applications in environment with free air flows - ScienceDirectScienceDirect](https://www.sciencedirect.com/science/article/abs/pii/S2352431620301115)
  * seems to be designed for low-frequency blocking?
  * looks like a combination of the pockets and half-wavelength pipes ideas, that's interesting
* [Dark acoustic metamaterials as super absorbers for low-frequency sound `|` Nature Communications](https://www.nature.com/articles/ncomms1758)
* [High-efficiency Ventilated Metamaterial Absorber at Low Frequency](https://arxiv.org/pdf/1801.03613.pdf)
* [Search `|` arXiv e-print repository](https://arxiv.org/search/?query=acoustic+metamaterial+absorbing&searchtype=all&abstracts=show&order=-announced_date_first&size=50)
* [[1608.04599] 3D Single-port Labyrinthine Acoustic Metamaterial](https://arxiv.org/abs/1608.04599)
* [[1405.7200] Acoustic metamaterial absorbers based on confined sonic crystals](https://arxiv.org/abs/1405.7200)
* [[1609.09561] Optimal Sound Absorbing Structures](https://arxiv.org/abs/1609.09561)
* [[1911.05969] Ultra-open High-efficiency Ventilated Metamaterial Absorbers with Customized Broadband Performance](https://arxiv.org/abs/1911.05969)
* [Demo acoustic metamaterial: acoustic enclosure - YouTube](https://www.youtube.com/watch?v=hMCfRHshjXc)
* [Advanced Metamaterials - YouTube](https://www.youtube.com/watch?v=s0UZ6-oeiIE)
* [3D Printed Acoustic Metamaterials: A New Frontier For Suppressors? - YouTube](https://www.youtube.com/watch?v=q9G4_OaEdoI)
* [Noise-eliminating materials `|` Yang Zhiyu - YouTube](https://www.youtube.com/watch?v=O57BX03Fg_0)


[//begin]: # "Autogenerated link references for markdown compatibility"
[geometry]: geometry "Geometry"
[3d-printing]: 3d-printing "3d Printing"
[//end]: # "Autogenerated link references"