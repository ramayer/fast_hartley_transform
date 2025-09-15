# FHT (Fast Hartley Transform)

* This implementation can be found in 
[Android](https://android.googlesource.com/platform/external/lame/+/c4cbe47910d2ece1617411206c6b5e4ffbe09360/libmp3lame/fft.c), 
[Panasonic televisions](https://archive.is/wip/FzpDv), 
[Siemens products](https://web.archive.org/web/20220123020714/https://assets.new.siemens.com/siemens/assets/api/uuid:ad102b2b-94d6-4cf8-bd60-73b8647dc689/readme-for-3rd-party-software-oss-mns.pdf), [LLVM's test suite](https://github.com/llvm/llvm-test-suite/blob/release/3.2.x/MultiSource/Benchmarks/MiBench/consumer-lame/fft.c), and popular numerical libraries like [UCSD PureData](https://github.com/pure-data/pure-data/blob/0.41-0test06/src/d_fft_mayer.c), [the fxt c++ library](https://github.com/mpoullet/fxt/blob/master/src/fht/fhtmayer.txt), the [Woolz Image Processing package](https://github.com/ma-tech/Woolz/blob/5ab012fff0fb50186d6ea8508f0d8b3063c45dc3/libAlg/AlgFourier.c#L4).


## Why It’s Important

The **Fast Hartley Transform (FHT)** is a close cousin of the Fast Fourier Transform (FFT), designed specifically for **real-valued input signals** (such as audio, sensor data, or images).  

Unlike FFTs—which produce complex numbers—the Hartley Transform uses only real values (`cos(x) + sin(x)`).  
This yields several key advantages:

* ⚡ **Better cache locality:** operates on a single real-valued array, improving instruction/data cache usage on CPUs with small on-chip caches.  
* 💾 **Lower memory footprint:** avoids storing and shuffling separate real and imaginary arrays.  
* 🧮 **Simplicity:** more straightforward than real-FFTs or DCTs, thanks to built-in symmetry and a compact implementation.  
* 🖩 **No dependency on fast trig hardware:** optionally uses a small `O(log n)` lookup table and stable on-the-fly recurrence to avoid costly `sin()`/`cos()` calls—especially useful on older embedded CPUs or microcontrollers with limited floating-point precision.

Because of these tradeoffs, this tiny FHT implementation I wrote as a college project became widely adopted over the decades in MP3 encoders, embedded devices, and numerical libraries.

---

## Summary

This implementation has quietly become one of the **most widely used Fast Hartley Transforms**, and appears in:

* **Android** ([source](https://android.googlesource.com/platform/external/lame/+/c4cbe47910d2ece1617411206c6b5e4ffbe09360/libmp3lame/fft.c))  
* **Panasonic televisions** ([source](https://contents.oss-src-distribution.panasonic.com/oss/tv/JPDTV18/liblame.html))  
* **Siemens products** ([source](https://assets.new.siemens.com/siemens/assets/api/uuid:ad102b2b-94d6-4cf8-bd60-73b8647dc689/readme-for-3rd-party-software-oss-mns.pdf))  
* **LLVM’s test suite** ([source](https://github.com/llvm/llvm-test-suite/blob/release/3.2.x/MultiSource/Benchmarks/MiBench/consumer-lame/fft.c))  
* **UCSD PureData**, the **fxt C++ math library**, the **Woolz Image Processing package**, and dozens more open source projects

---

## Background

The **Hartley Transform** is mathematically similar to the **Fourier Transform**, except it avoids complex numbers by using the kernel:

     cas(x) = cos(x) + sin(x)



This produces real-valued outputs and enables optimizations not possible with traditional FFTs. The FHT can be computed in `O(n log n)` time, like the FFT, but its single-array real-only design often runs **faster on real data**.

---

## Original Release

* [comp.lang.c post (1993)](https://groups.google.com/g/comp.lang.c/c/Gs3APm2Dva0/m/GF7vVzIMAVsJ)  
  ([archive1](https://archive.is/rIp4B) · [archive2](https://web.archive.org/web/20240331052518/https://groups.google.com/g/comp.lang.c/c/Gs3APm2Dva0/m/GF7vVzIMAVsJ))
* [follow-up discussion](https://groups.google.com/g/comp.lang.c/c/t2IDPzA_mgM/m/xeE53C7LD6YJ)  
  ([archive1](https://archive.is/dZzER) · [archive2](https://web.archive.org/web/20240331052750/https://groups.google.com/g/comp.lang.c/c/t2IDPzA_mgM/m/xeE53C7LD6YJ))

---

## Discussion and Analysis

* [McGill “How fiddle~ Works” (2016)](https://www.music.mcgill.ca/~ich/classes/mumt621_11/final%20projects/final/Report.pdf) — describes this implementation  
* [Performance evaluation of FFT routines](https://www.researchgate.net/publication/2936699_Performance_Evaluation_of_FFT_Routines_Machine_Independent_Serial_Programs)  
* [citeseerx comparison](https://citeseerx.ist.psu.edu/document?repid=rep1&type=pdf&doi=9389e68c437891c7fa51eeccef286a50afbbc033)  
* [Stack Overflow discussion](https://stackoverflow.com/questions/16087290/ron-mayer-fft-convolution-algorithm)

---

## Historical Notes

* Widely circulated on Usenet starting in 1993  
* Incorporated in MP3 encoders, PureData, and DSP libraries through the 1990s–2000s  
* Mentioned in patent debates:  
  * [Fedora legal list](https://lists.fedoraproject.org/pipermail/legal/2010-May/001272.html)  
  * [Debian collab-qa](https://alioth-lists-archive.debian.net/pipermail/collab-qa-commits/2012-June/002266.html)  
* Frequently “re-discovered” over the years ([example](https://news.ycombinator.com/item?id=27386319))

---

## License

Originally released to the public domain via Usenet in 1993.

---

## Historical Timeline

| Year | Event |
|------|-------|
| 1770s | Euler - probable inventor of the fourier transform. |
| 1800s | Gauss - probable inventor of the FFT (fast fourier transform) - and used it on paper |
| 1920s | Hartley - probable inventor of the hartley transform. |
| 1983 | Bracewell implements a fast Hartley Transform |
| 1984 | Bracewell [patents](https://patents.google.com/patent/US4646256A/fr) a Fast Hartley Transform  |
| 1990s | this FHT implementation adopted in many image and signal processing libraries |
| 2000s | Incorporated into mobile and embedded DSP systems |
| 2010s | Used in Android audio stack for real-time processing |
| Today | Still used as a lightweight real-valued FFT alternative |


## Forks and references. 

* https://www.geocities.ws/ResearchTriangle/8869/fft_summary.html

* 1995 packaging by Peter J. McKinney for comp.lang.c++ https://groups.google.com/g/comp.lang.c++/c/hQguc63Xbv4/m/2h6Ya6d7sx8J
* https://github.com/Venetian/MayerFFT

* A port to Forth: https://web.archive.org/web/20070702230415/http://home.claranet.nl/users/mhx/fft_c.frt 
* A port to Java: https://github.com/zhuker/lamejs/blob/master/src/main/java/mp3/FFT.java 

* [Woolz Image Processing software, via Bill Hill of University of Edinburgh's 2012 fork](https://www.emouseatlas.org/emap/analysis_tools_resources/software/woolz/html_Core/AlgFourier_8c.html), [src](https://github.com/ma-tech/Woolz/blob/5ab012fff0fb50186d6ea8508f0d8b3063c45dc3/libAlg/AlgFourier.c#L43), [archive](https://web.archive.org/web/20240331174745/https://www.emouseatlas.org/emap/analysis_tools_resources/software/woolz/html_Core/AlgFourier_8c.html) [archive2](https://archive.is/vFKpB)


* The [LAME mp3 library](https://github.com/lameproject/lame/blob/master/libmp3lame/fft.c)

* https://svn.blender.org/svnroot/bf-blender/branches/blender2.4/extern/libmp3lame/fft.c - Blender's MP3 support.

* https://www.netlib.org/performance/html/fft.intro.html - Netlib  [archive](https://archive.is/wip/vdKn0)

* fxt C++ library: https://www.jjj.de/fxt/,  https://github.com/mpoullet/fxt/blob/master/src/fht/fhtmayer.txt
* Jamoma C++ Port - https://api.jamoma.org/mayer__fft_8cpp_source.html , [archive](https://archive.is/wip/odQnv)

* UCSD PureData - https://github.com/pure-data/pure-data/blob/0.41-0test06/src/d_fft_mayer.c
 https://lists.puredata.info/pipermail/pd-list/2002-04/005660.html

* Autotalent - https://github.com/olilarkin/autotalent/blob/master/mayer_fft.c

* LLVM's test suite - https://github.com/llvm/llvm-test-suite/blob/release/3.2.x/MultiSource/Benchmarks/MiBench/consumer-lame/fft.c

* https://www.researchgate.net/publication/2936699_Performance_Evaluation_of_FFT_Routines_Machine_Independent_Serial_Programs

* libmicdroid - https://github.com/intervigilium/libmicdroid/blob/master/autotalent/mayer_fft.c

* https://www.leidinger.net/lame/doxy/html/fft_8c-source.html (archive)[https://archive.is/wip/CZlNW]

* https://labath.me/docs/C/C_lang.html (archive)[https://archive.is/wip/tqNS7]

* Ajay Shah's 1995 Netlib / Numcomp-free fork- https://www.netlib.org/c/numcomp-free-c (archive)[https://archive.is/wip/TN4eO]

* The [fxt C++ math package of 1997 by Joerg Arndt from www.spektracom.de](https://www.ibiblio.org/pub/Linux/docs/LSM/LSM.1999-08-29), [archive](https://archive.is/wip/oZxMW) , https://github.com/mpoullet/fxt/blob/master/src/fht/fhtmayer.txt

* Stack overflow discussion: https://stackoverflow.com/questions/16087290/ron-mayer-fft-convolution-algorithm

* [Linux Announce mailinglist of Joerg Arndt's 1999 C++ fork](https://www.mail-archive.com/linux-announce@senator-bedfellow.mit.edu/msg00143.html), [archive](https://archive.is/wip/549MP)

* Fossies: https://fossies.org/linux/lame/libmp3lame/fft.c

* [A Hungarian translation](https://hr.glosbe.com/en/hr/Hartley%20transform), [archive1](https://web.archive.org/web/20240331184541/https://hr.glosbe.com/en/hr/Hartley%20transform), [archive2](https://archive.is/hS1vO)

* ["How fiddle∼ Works" paper from Nathan Whetsell from music.mcgill.ca in 2016](https://www.music.mcgill.ca/~ich/classes/mumt621_11/final%20projects/final/Report.pdf) [archive](https://web.archive.org/web/20160109024217/https://www.music.mcgill.ca/~ich/classes/mumt621_11/final%20projects/final/Report.pdf) (so apparently it was used in the fiddle~ object in the https://en.wikipedia.org/wiki/Max_(software) software)

* [](https://archive.is/wip/wYej5)

* [Android.googlesource.com](https://android.googlesource.com/platform/external/lame/+/c4cbe47910d2ece1617411206c6b5e4ffbe09360/libmp3lame/fft.c), [archive](https://archive.is/wip/ZQXbL)

* [Siemens credits the project in their Readme for Third Party OSS Software](https://assets.new.siemens.com/siemens/assets/api/uuid:ad102b2b-94d6-4cf8-bd60-73b8647dc689/readme-for-3rd-party-software-oss-mns.pdf) [archive](https://web.archive.org/web/20220123020714/https://assets.new.siemens.com/siemens/assets/api/uuid:ad102b2b-94d6-4cf8-bd60-73b8647dc689/readme-for-3rd-party-software-oss-mns.pdf)

* [Panasonic's televisions](https://contents.oss-src-distribution.panasonic.com/oss/tv/JPDTV18/liblame.html), [archive](https://archive.is/wip/FzpDv)

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


* Large Scentific Calculations on Dedicted Clusters of Workstations
https://citeseerx.ist.psu.edu/document?repid=rep1&type=pdf&doi=939b78b97170b99f62fdb4c6d8707fae38bda388, 
https://archive.is/dynGg

* Some [Bosch/Mitsubishi copyright disclosure](https://oss.bosch-cm.com/download/Mitsubishi/6871_241205/OSS_Disclosure_Document_6871_241205_MMC_GEN4.pdf)

* Some [SK Telecom project](https://opensource.sktelecom.com/compliance_artifacts/cookiz_watch_joon/ios/3.41/Cookiz_iOS_3.41_OSS_Notice.html), [archive](https://archive.ph/wip/jkkLM)

* Debian's copyright page: https://browse.dgit.debian.org/praat.git/plain/debian/copyright?h=debian/6.4.25%2Bdfsg-1

*  The [Jump3r Java project](https://www.scribd.com/document/773742426/jump3r-LICENSE)

## Old patent debates

* https://lists.fedoraproject.org/pipermail/legal/2010-May/001272.html
* https://alioth-lists-archive.debian.net/pipermail/collab-qa-commits/2012-June/002266.html

* And yes, it's silly that it was ever patented, considering [amateurs re-discover it every few years](https://news.ycombinator.com/item?id=27386319)
