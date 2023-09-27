**Introduction**

This section provides many details on modeling polarons using electronic structure theory, especially with density functional theory (DFT). I assume you know how to run DFT calculations, but want to know more about modeling polarons. We discuss the challenges in modeling polarons and how to overcome these challenges. You’ll find advice, ideas, and some references that may help get you started.

![m-BiVO4_sample_polaron](https://github.com/Deskins-group/Modeling-Polarons/assets/16135778/9cc56212-3de7-437d-8cd0-bfeb84fa41ce)

A polaron in BiVO<sub>4</sub> with electrons localizing in a d-orbital. Geometric distortions occur around the polaron site.

**Background**

There are two broad classes of charge carriers in semiconductors: polarons and bands. Polarons occur as electrons or holes in semiconductors distort the lattice and become localized within the lattice. This slows down the mobility of charge carriers relative to bands, and leads to a distortion around the polaron site. Both large and small polarons occur, depending on the extent of the distortion, and each has unique properties. Furthermore, polarons may be negatively charged (electrons) or positively charged (holes). Several reviews exist on the study of polarons.

- https://en.wikipedia.org/wiki/Polaron
- Devreese, Jozef T. “Polarons.” Encycl. Appl. Phys. 14.cond-mat/0004497 (1996): 383-409.
- Alexandrov, Alexandre S., and Jozef T. Devreese. Advances in polaron physics. Vol. 159. Berlin: Springer, 2010.
- Shluger, A. L., and A. M. Stoneham. “Small polarons in real crystals: concepts and problems.” Journal of Physics: Condensed Matter 5.19 (1993): 3049.
- Emin, David. Polarons. Cambridge University Press, 2013.
- Franchini, C., Reticcioli, M., Setvin, M., & Diebold, U. (2021). Polarons in materials. Nature Reviews Materials, 0123456789.

Polarons may occur in materials as excess electrons or holes form. Photoexcitation may create polarons, where excited electrons and holes are created. Defects in a material may also create polarons, either excess electrons or a deficit of electrons (hole). For example, formation of an oxygen vacancy in a metal oxide such as TiO2 creates excess electrons that may localize as polarons. A dopant, like Nb in TiO2, may also create an excess electron that forms a polaron.

The nature and properties of polarons (such as size, mobility, and stability) are all important, as they strongly influence the applicability of a material for a given application. For example, polarons may limit or determine the conductivity within a semiconductor used in electronic devices. Polarons may also enable reduction or oxidation reactions, such as in photocatalysis. Polarons may also play an important role in geochemical processes that occur with minerals. Thus, the study of characterization of polarons is an on-going area of research.

Polarons can be modeled using electronic structure methods, such as density functional theory. Challenges, however, do exist in modeling polarons, as discussed here. An example polaron in TiO2 is shown below. Note that the electron polaron exists as a d orbital localized on a Ti atom. Further examples abound in the literature, and polarons have been observed in many materials, such as HfO2, FeO, FePO4, BaTiO3, BiVO4, and others. A literature search (such as “polarons density functional theory”) will give many examples of modeling polarons.

**Challenges**

Density functional theory (DFT) is one of the most popular electronic structure methods due to its good balance between accuracy and speed. Other theoretical methods exist[^Franc], but DFT is the most common method for atomistic material simulations, due to its balance of accuracy and computational time. A central problem in modeling polarons with DFT is the delocalization of electrons that may occur due to self-interaction errors. Self-interaction errors [^sie] occur with many common exchange-correlation potentials, leading to the wrong description of polarons in many materials.

[^Franc]: Franchini, C., Reticcioli, M., Setvin, M., & Diebold, U. (2021). Polarons in materials. Nature Reviews Materials, 0123456789.
[^sie]: Pacchioni, Gianfranco. “Modeling doped and defective oxides in catalysis with density functional theory methods: Room for improvements.” The Journal of chemical physics 128.18 (2008): 182505 ;
  Ganduglia-Pirovano, M. Veronica, Alexander Hofmann, and Joachim Sauer. “Oxygen vacancies in transition metal and rare earth oxides: Current state of understanding and remaining challenges.” Surface science reports 62.6 (2007): 219-270. ;
  Huang, Patrick, and Emily A. Carter. “Advances in correlated electronic structure methods for solids, surfaces, and nanostructures.” Annu. Rev. Phys. Chem. 59 (2008): 261-290)

See for example below two different DFT solutions for TiO2. One solution (with self-interaction errors) leads to an unpaired electron being delocalized throughout the simulation cell. The proper solution has the electron localized on a Ti atom, forming a polaron state. If one is to model polarons, then the ‘correct’ method must be chosen in order to avoid an incorrect description of polarons.

A delocalized solution in TiO2, where an unpaired electron is spread throughout the simulation cell.

A localized solution in TiO2, where a polaron forms with an electron localized on a Ti atom.


While DFT often fails to properly model polarons, methods do exist which enable localization of polarons. The DFT+U method [^dftu] is one of the common approaches to enabling charge localization. DFT+U adds a correction term (hence +U) to DFT calculations to help remove self-interaction errors. It requires little more computational time than standard DFT calculations, and is therefore one of the most popular methods for modeling polarons. A different approach uses hybrid functionals [^hse06]. Such functionals also enable localization of polarons, but often require considerable more computational time. In any case, an appropriate method must be chosen so that ‘correct’ localization of polarons occurs.

[^dftu]: Dudarev, S. L., Botton, G. A., Savrasov, S. Y., Humphreys, C. J., & Sutton, A. P. (1998). Electron-energy-loss spectra and the structural stability of nickel oxide: An LSDA+U study. Physical Review B, 57(3), 1505–1509. ; Tolba, S. A., Gameel, K. M., Ali, B. A., Almossalami, H. A., & Allam, N. K. (2018). The DFT+U: Approaches, Accuracy, and Applications. Density Functional Calculations – Recent Progresses of Theory and Application, 3–30. ; Capdevila-Cortada, M., Łodziana, Z., & López, N. (2016). Performance of DFT+ U Approaches in the Study of Catalytic Materials. ACS Catalysis, 6(12), 8370–8379. ; Himmetoglu, B., Floris, A., de Gironcoli, S., & Cococcioni, M. (2014). Hubbard-corrected DFT energy functionals: The LDA+U description of correlated systems. International Journal of Quantum Chemistry, 114(1), 14–49.

[^hse06]: Deák, P., Aradi, B., & Frauenheim, T. (2011). Polaronic effects in TiO2 calculated by the HSE06 hybrid functional: Dopant passivation by carrier self-trapping. Physical Review B, 83(15), 155207. ; Finazzi, E., Di Valentin, C., Pacchioni, G., & Selloni, A. (2008). Excess electron states in reduced bulk anatase TiO2: Comparison of standard GGA, GGA+U, and hybrid DFT calculations. The Journal of Chemical Physics, 129(15), 154113. ; De Lile, J. R., Kang, S. G., Son, Y.-A., & Lee, S. G. (2019). Investigating Polaron Formation in Anatase and Brookite TiO2 by Density Functional Theory with Hybrid-Functional and DFT + U Methods. ACS Omega, 4(5), 8056–8064.

Even if a method is applied that overcomes self-interaction errors, polaron formation is not guaranteed. For a given level of theory there may be several stable or metastable solutions[^meta]. The initial structure and wavefunction may all influence whether polarons form. Key characteristics of a polaron are the distortion of bonds between the polaron site and neighboring atoms, as well as the occupancy (or vacancy for holes) of electronic orbitals. The polaron essentially breaks the symmetry of the crystal as the distortions and electrons are centered around the polaron site. Simply using default settings or perfect crystals may not enable polaron formation. The simulation input must be chosen so that initial geometries and/or electronic orbitals mimic a polaron to enable convergence to a stable polaron solution.

[^meta]: Meredig, B., Thompson, A., Hansen, H. A., Wolverton, C., & van de Walle, A. (2010). Method for locating low-energy solutions within DFT+U. Physical Review B, 82(19), 195128

**Approaches to Modeling Polarons**

As we discussed, there are several challenges to modeling polarons. Simply using DFT+U or hybrid functionals does not guarantee polaron formation. A deliberate approach must be taken, or polaron formation may occur in a random or happenstance manner. A general strategy to modeling polarons can be summarized as: (1) Choose a method to overcome self-interaction errors (e.g. DFT+U or hybrid functionals). (2) Choose initial settings/input that help with convergence to a localized polaron. We discuss several approaches below that help with polaron convergence.

*Bond Distortion Method*

This is one of the simplest, easiest ways to enable charge localization. An analysis of this method and further discussion can be found in our paper[^pham]. This method has several advantages, as it is easy to implement and does not rely on any particular modeling code. It can be used with many different codes, e.g. VASP, CP2K, Siesta, etc. The basic premise of this method is to create initial geometries that look like polaron geometries, and this helps ensure convergence to localized solutions. Rather than using a symmetrical crystal as the initial structure, in this method the initial geometries have lengthened bonds around the polaron site. Since the structure ‘looks’ like a polaron, convergence to a localized solution more readily occurs. We found that this method is very efficient (more than the electron attractor method) and usually converges to polarons just fine. Scripts and sample input files to create initial geometries with distorted bonds can be found [here](https://github.com/Deskins-group/Other-Files/tree/master/Polaron-Strategies).

[^pham]: Pham, T. D., & Deskins, N. A. (2020). Efficient Method for Modeling Polarons Using Electronic Structure Methods. Journal of Chemical Theory and Computation, 16(8), 5264–5278.


In the bond distortion method the initial geometry has elongated bonds around the desired polaron site. This initial geometry ‘looks’ like a polaron so helps ensure convergence to a localized state.

*Electron Attractor Method*

This approach aims to attract electrons to a particular atomic site to enable polaron localization. More positive charge is placed somewhere in the lattice, and since electrons are attracted to positive charge the electrons may localize at that site. The extra positive charge can for instance be obtained by carefully choosing the pseudopotential, which represents the nucleus and core electrons. For instance, Ti has an atomic number of 22, meaning that the nucleus has 22 protons. V has an atomic number of 23 and has a slightly more positive nucleus than Ti. When modeling TiO2, the pseudopotential for one Ti atom can be replaced with a V pseudopotential. When the simulation is run, an excess electron should in principle be attracted to the V site because of its larger positive charge. Once a wavefunction and geometry with localized charge is obtained, then the original pseudopotential can be used (i.e. Ti instead of V). We found that this method can be tricky to use and is slower than the bond distortion method. Sometimes it works, while other times it does not. It also does not always converge to lowest energy states, so use it with care.


With the electron attractor method a more positively charged nucleus (like V instead of Ti) is put in the cell so that electrons may be attracted to that atomic site.

*Orbital Occupancy/Control*

If one can choose which orbitals are occupied by electrons, then one can choose to put an extra electron at a particular site and orbital. Again, if the initial wavefunction ‘looks’ like the localized wavefunction, then convergence to the desired localized solution could occur. A method to control orbital occupancy has been implemented in VASP[^orb]. Other codes may also allow specification or control of the initial orbitals. Constrained DFT[^constrained] adds a constraining potential, and can also be used to control charge/spin.

[^orb]: Allen, J. P., & Watson, G. W. (2014). Occupation matrix control of d- and f-electron localisations using DFT + U. Phys. Chem. Chem. Phys., 16(39), 21016–21031 ; https://www.chemistry.tcd.ie/staff/people/gww/gw_new/research/methodology/

[^constrained]: Kaduk, B., Kowalczyk, T., & Van Voorhis, T. (2012). Constrained Density Functional Theory. Chemical Reviews, 112(1), 321–370. ; Ma, H., Wang, W., Kim, S., Cheng, M., Govoni, M., & Galli, G. (2020). PyCDFT: A Python package for constrained density functional theory. Journal of Computational Chemistry, 41(20), 1859–1867.

**Calculating Other Properties**

Beyond simply obtaining localized polaron solutions, there exist many properties of interest of such polarons. Below are discussed a few properties that can be calculated from electronic structure calculations.

*Self-Trapping Energy*

Determining the stability of a polaron is important, and can be calculated from DFT. Several examples in the literature[^stab] illustrate such calculations. The self-trapping energy is simple the difference in energy between the localized solution and delocalization solution. If the localized solution is energetically preferred, then polarons are stable in that material. If the delocalized solution is energetically preferred, then polarons are unstable in that material.

[^stab]: Muñoz Ramo, D., Shluger, A. L., Gavartin, J. L., & Bersuker, G. (2007). Theoretical prediction of intrinsic self-trapping of electrons and holes in monoclinic HfO2. Physical Review Letters, 99(15), 1–4.; Janotti, A., Franchini, C., Varley, J. B., Kresse, G., & Van de Walle, C. G. (2013). Dual behavior of excess electrons in rutile TiO2. Physica Status Solidi – Rapid Research Letters, 7(3), 199–203.


Self-trapping energies can be calculated by comparing the energies of delocalized and localized solutions.

*Polaron Location*

Related to polaron stability is determining the preferred location of a polaron. The preferred location has implications on polaron mobility and reactivity (such as in photocatalysis). Especially near surfaces or dopants, there may be several possible atomic sites where the polaron may locate. By modeling a polaron at different sites, the energy of a polaron at these sites can be mapped out. Several examples of this are available.[^loc]

[^loc]: Deskins, N. A., Rousseau, R., & Dupuis, M. (2009). Localized electronic states from surface hydroxyls and polarons in TiO 2(110). Journal of Physical Chemistry C, 113(33). ; Deskins, N. A., Rousseau, R., & Dupuis, M. (2011). Distribution of Ti3+ surface sites in reduced TiO2. Journal of Physical Chemistry C, 115(15) ; Kowalski, P. M., Camellone, M. F., Nair, N. N., Meyer, B., & Marx, D. (2010). Charge Localization Dynamics Induced by Oxygen Vacancies on the TiO2 (110) Surface. Physical Review Letters, 105(14), 146405. ; Yim, C. M., Watkins, M. B., Wolf, M. J., Pang, C. L., Hermansson, K., & Thornton, G. (2016). Engineering Polarons at a Metal Oxide Surface. Physical Review Letters, 117(11), 116402.

The relative stability of polarons at different Ti atoms at the surface of TiO2 rutile (110). The number/color scale corresponds to energies in eV. The * indicates the most stable location of the polaron (0 eV).

*Polaron Mobility*

Since polarons exist as localized states, they do not move as bands do. Rather they hop from one site to another in an activated process. By calculating energies for the initial, final, and transition state, the activation barrier can be determined. From all this, the rate of charge hopping can be calculated, including charge mobility and conductivity. Coupling between the initial and final states may also influence the hopping rate. Examples in the literature illustrate how to calculate polaron mobility.[^mob]

[^mob]:  N. A., & Dupuis, M. (2007). Electron transport via polaron hopping in bulk TiO2: A density functional theory characterization. Physical Review B, 75(19), 195212. ; Rosso, K. M., Smith, D. M. A., & Dupuis, M. (2003). An ab initio model of electron transport in hematite (α-Fe2O3) basal planes. The Journal of Chemical Physics, 118(14), 6455–6466. ; Maxisch, T., Zhou, F., & Ceder, G. (2006). Ab initio study of the migration of small polarons in olivine Li x FePO 4 and their association with lithium ions and vacancies. Physical Review B, 73(10), 104301. ; Natanzon, Y., Azulay, A., & Amouyal, Y. (2020). Evaluation of Polaron Transport in Solids from First-principles. Israel Journal of Chemistry, 60(8–9), 768–786. ; Liu, T., Pasumarthi, V., Laporte, C., Feng, Z., Li, Q., Yang, J., Li, C., & Dupuis, M. (2018). Bimodal hole transport in bulk BiVO4 from computation. Journal of Materials Chemistry A: Materials for Energy and Sustainability, 6, 3714–3723.


The activation energy for polaron hopping from one site to another can be calculated by determining the energy as the electron (or hole) moves from the initial site (reaction coordinate 0) to the final site (reaction coordinate 1).


