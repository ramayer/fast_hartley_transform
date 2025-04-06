# FHT (Fast Hartley Transform)


## Original release

* https://groups.google.com/g/comp.lang.c/c/Gs3APm2Dva0/m/GF7vVzIMAVsJ [archive1](https://archive.is/rIp4B), [archive2](https://web.archive.org/web/20240331052518/https://groups.google.com/g/comp.lang.c/c/Gs3APm2Dva0/m/GF7vVzIMAVsJ)
* https://groups.google.com/g/comp.lang.c/c/t2IDPzA_mgM/m/xeE53C7LD6YJ [archive1](https://archive.is/dZzER)  [archive2](https://web.archive.org/web/20240331052750/https://groups.google.com/g/comp.lang.c/c/t2IDPzA_mgM/m/xeE53C7LD6YJ)



## Forks and references. 

* https://www.geocities.ws/ResearchTriangle/8869/fft_summary.html

* 1995 packaging by Peter J. McKinney for comp.lang.c++ https://groups.google.com/g/comp.lang.c++/c/hQguc63Xbv4/m/2h6Ya6d7sx8J
* https://github.com/Venetian/MayerFFT


* A port to Forth: https://web.archive.org/web/20070702230415/http://home.claranet.nl/users/mhx/fft_c.frt 
* A port to Java: https://github.com/zhuker/lamejs/blob/master/src/main/java/mp3/FFT.java 

* [Woolz Image Processing software, via to Bill Hill of University of Edinburgh's 2012 fork](https://www.emouseatlas.org/emap/analysis_tools_resources/software/woolz/html_Core/AlgFourier_8c.html), [src](https://github.com/ma-tech/Woolz/blob/5ab012fff0fb50186d6ea8508f0d8b3063c45dc3/libAlg/AlgFourier.c#L43), [archive](https://web.archive.org/web/20240331174745/https://www.emouseatlas.org/emap/analysis_tools_resources/software/woolz/html_Core/AlgFourier_8c.html) [archive2](https://archive.is/vFKpB)

* https://svn.blender.org/svnroot/bf-blender/branches/blender2.4/extern/libmp3lame/fft.c - Blender's MP3 support.

* https://www.netlib.org/performance/html/fft.intro.html - Netlib 

* Jamoma - https://api.jamoma.org/mayer__fft_8cpp_source.html 

* UCSD PureData - https://github.com/pure-data/pure-data/blob/0.41-0test06/src/d_fft_mayer.c
 https://lists.puredata.info/pipermail/pd-list/2002-04/005660.html

* Autotalent - https://github.com/olilarkin/autotalent/blob/master/mayer_fft.c

* LLVM's test suite - https://github.com/llvm/llvm-test-suite/blob/95a9f0d0b45056274f0bb4b0e0dd019023e414dc/MultiSource/Benchmarks/MiBench/consumer-lame/fft.c

* https://www.researchgate.net/publication/2936699_Performance_Evaluation_of_FFT_Routines_Machine_Independent_Serial_Programs

* libmicdroid - https://github.com/intervigilium/libmicdroid/blob/master/autotalent/mayer_fft.c

* https://www.leidinger.net/lame/doxy/html/fft_8c-source.html

* https://labath.me/docs/C/C_lang.html

* Ajay Shah's 1995 Netlib / Numcomp-free fork- https://www.netlib.org/c/numcomp-free-c

* The [fxt C++ math package of 1997 by Joerg Arndt from www.spektracom.de](https://www.ibiblio.org/pub/Linux/docs/LSM/LSM.1999-08-29)

* Stack overflow discussion: https://stackoverflow.com/questions/16087290/ron-mayer-fft-convolution-algorithm

* [Joerg Arndt's 1999 fork](https://www.mail-archive.com/linux-announce@senator-bedfellow.mit.edu/msg00143.html)

* Fossies: https://fossies.org/linux/lame/libmp3lame/fft.c

* [A Hungarian translation](https://hr.glosbe.com/en/hr/Hartley%20transform), [archive1](https://web.archive.org/web/20240331184541/https://hr.glosbe.com/en/hr/Hartley%20transform), [archive2](https://archive.is/hS1vO)

* ["How fiddle∼ Works" paper from Nathan Whetsell from music.mcgill.ca in 2016](https://www.music.mcgill.ca/~ich/classes/mumt621_11/final%20projects/final/Report.pdf) [archive](https://web.archive.org/web/20160109024217/https://www.music.mcgill.ca/~ich/classes/mumt621_11/final%20projects/final/Report.pdf) (so apparently it was used in the fiddle~ object in the https://en.wikipedia.org/wiki/Max_(software) software)


* [Android.googlesource.com](https://android.googlesource.com/platform/external/lame/+/c4cbe47910d2ece1617411206c6b5e4ffbe09360/libmp3lame/fft.c)

* [Siemens credits the project in their Readme for Third Party OSS Software](https://assets.new.siemens.com/siemens/assets/api/uuid:ad102b2b-94d6-4cf8-bd60-73b8647dc689/readme-for-3rd-party-software-oss-mns.pdf) [archive](https://web.archive.org/web/20220123020714/https://assets.new.siemens.com/siemens/assets/api/uuid:ad102b2b-94d6-4cf8-bd60-73b8647dc689/readme-for-3rd-party-software-oss-mns.pdf)

* [Panasonic's ](https://contents.oss-src-distribution.panasonic.com/oss/tv/JPDTV18/liblame.html)

## Old discussions

* https://www.music.mcgill.ca/~ich/classes/mumt621_11/final%20projects/final/Report.pdf

>> The particular implementation of the DHT used in fiddle∼ appears to be based on code written by
one Ron Mayer sometime in 1993. Surprisingly, the primary reference describing this code—(Mayer 1993)—
refers to an Internet message board post (in fact a copy of a message board post). It appears that in many
applications the “Mayer FHT” has been superseded by modern algorithms. Mayer himself suggests the
whimsically titled Fastest Fourier Transform in the West (FFTW) for general purpose applications (Mayer).

* https://citeseerx.ist.psu.edu/document?repid=rep1&type=pdf&doi=9389e68c437891c7fa51eeccef286a50afbbc033 - analysis of the algorithm comparing it to other FFTs.

* [a reference to a related project from a medical article](https://pdfslide.net/documents/fast-hartley-transforms-for-image-processing.html?page=3), [archive](https://archive.is/BcQUO)

* Used by [Design and Implementation of an Acoustical
Transmission Protocol by David Erman of Blekinge Institute of Technology in 2002](https://www.diva-portal.org/smash/get/diva2:832972/FULLTEXT01.pdf) for the RoboCup Sony Legged Robot League, [alt link](https://www.researchgate.net/profile/Mohamed-Mourad-Lafifi/post/What_amount_of_data_given_the_constraints_of_the_hardware_in_the_AIBO_robot/attachment/5abf5e7fb53d2f63c3c311f6/AS%3A610185664004096%401522491007373/download/Design+and+Implementation+of+an+Acoustical+Transmission+Protocol.pdf)

* In Debian's copyright pages for Audacity: 
https://tracker.debian.org/media/packages/a/audacity/copyright-2.4.2dfsg0-5


## Old patent debates

* https://lists.fedoraproject.org/pipermail/legal/2010-May/001272.html
* https://alioth-lists-archive.debian.net/pipermail/collab-qa-commits/2012-June/002266.html

* And yes, it's silly that it was ever patented, considering [amateurs re-discover it every few years](https://news.ycombinator.com/item?id=27386319)
