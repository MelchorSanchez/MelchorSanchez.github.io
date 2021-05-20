---
title: Automatic Protein-Ligand interaction analysis
subtitle: The new release of PLIP (Protein Ligand Interaction Profiler)
layout: post
group: blog
comments: true
author : Melchor Sanchez-Martinez
date: 2021-05-22
tags: [PLIP, python, file-parsing, protein-ligand, interaction_analysis]
categories: [CADD, Cheminformatics, SBDD, DrugDesign]
---
<!-- excerpt-start -->
The new release of [**PLIP**](https://github.com/pharmai/plip), one of the most useful and complete tools to analyze protein-ligand interactions [has been recently published](https://academic.oup.com/nar/advance-article/doi/10.1093/nar/gkab294/6266421#246639495) in [Nucleic Acids Research](https://academic.oup.com/nar/) <!-- excerpt-end -->  , where it was also published the [original publication](https://academic.oup.com/nar/article/43/W1/W443/2467865?searchresult=1) in 2015. The **-Ligand Interaction Profiler (PLIP)** allows you easily analyze non-covalent interactions between biological macromolecules and their ligands based on PDB files. It can be used as a {web server](https://plip-tool.biotec.tu-dresden.de/plip-web/plip/index) or locally. To use it locally it can be done through a containerized Image or installing it via PyPy or from the source code ([check the different options](https://github.com/pharmai/plip)).

PLIP was originally developed by [Schroeder's group](https://tu-dresden.de/cmcb/biotec/forschungsgruppen/schroeder) from the [Biotechnology Center](https://tu-dresden.de/cmcb/biotec) of the Technische Universität Dresden (https://tu-dresden.de). Since April 2020 PLIP is officially maintained by [PharmAI GmbH](https://www.pharm.ai).

<figure>
  <img src="https://oup.silverchair-cdn.com/oup/backfile/Content_public/Journal/nar/PAP/10.1093_nar_gkab294/1/m_gkab294gra1.jpeg?Expires=1623703314&Signature=DvUQqbHT5OKfDznXWyCG-G8QH1UTsUITRP19g-aij8tZ-XIcQrSi2oT-KvdOlRBWYmiwpEvLf1QAWgM1GTFBjOZUC36NR-AWpt4QEgNl1GmRAQVm7xGKXr9kxSDPEVEpfeHTjFiUkM3A6kaaGGZsgew-msRHhZXL4Ti8iEspHgCbdAc1E878RhfLSlprXjgWnvLFHOiocrQ2OYGC8lTU2Wc2WLxydB67tWyhYyICxgDW4jS5gnQWUAjYbnbBmWFe6EO75k5rhAx7pjp7Ap6tjah6BdB0odqrW9PaKNRoUUQcXdu-mOIbW1ByiKR87bVbEx1M3l4pH8JvDmvtXTfZFg__&Key-Pair-Id=APKAIE5G5CRDK6RD3PGA" alt="Graphical abstract of [2021 PLIP publication](https://academic.oup.com/nar/advance-article/doi/10.1093/nar/gkab294/6266421#246639495)" title="Graphical abstract of [2021 PLIP publication](https://academic.oup.com/nar/advance-article/doi/10.1093/nar/gkab294/6266421#246639495)" class="img-responsive">
  <figcaption>Graphical abstract of [2021 PLIP publication](https://academic.oup.com/nar/advance-article/doi/10.1093/nar/gkab294/6266421#246639495)</figcaption>
</figure>
<p style="font-size:12px;color:darkgrey" class="text-center">*Graphical abstract of [2021 PLIP publication](https://academic.oup.com/nar/advance-article/doi/10.1093/nar/gkab294/6266421#246639495)*</p>

I discovered PLIP less than a year after its original publication, around November 2016. Since then I have been regularly using it in almost a (daily basis at work)[/publications]. There are some reasons I like it. First of all it is quite precise. It is able to reproduce the reported binding modes of different structures. Then, it is code in python and open source available in GitHub. So you can read the code, understand the code and uderstand what the code does. It is not a black box. Moreover, as you can easily acces the code, you can custom it. For instance you can custom the pymol representation (it uses the Protein PDB file numbering but maybe you want to change it to match the original protein sequence numbering) or the different applied cutoffs. Now you can change the cutoffs, temporary, as a command line argument when executing the code (what is a really a nice addition), but in the initial versions you had to modify the config.py file (actually this is the way to permanently change it). For instance I used to change the BD_DIST (maximum distance to include binding site residues), the Hydrogen bond distance cutoff or the \pi stacking distance. PLIP determines interactions between ligand-protein residues based on distances and/or angles, depending on the measured interaction.

I also like PLIP because it is coupled with pymol and as an oupit you can parsable files, png images of the protein-ligand interactions and also pymol sessions that then you can play with.

~~~html

~~~
<p style="font-size:12px;color:darkgrey" class="text-center">*Pymol.py script modified to change the PDB numbering*</p>



~~~html
# Thresholds for detection (global variables)
BS_DIST = 10.0 #7.5  # Determines maximum distance to include binding site residues
AROMATIC_PLANARITY = 5.0  # Determines allowed deviation from planarity in aromatic rings
MIN_DIST = 0.5  # Minimum distance for all distance thresholds
# Some distance thresholds were extended (max. 1.0A) if too restrictive too account for low-quality structures
HYDROPH_DIST_MAX = 4.0  Distance cutoff for detection of hydrophobic contacts
HBOND_DIST_MAX = 3.5 #4.1  # Max. distance between hydrogen bond donor and acceptor (Hubbard & Haider, 2001) + 0.6 A
HBOND_DON_ANGLE_MIN = 100  # Min. angle at the hydrogen bond donor (Hubbard & Haider, 2001) + 10
PISTACK_DIST_MAX = 6.0 #5.5  # Max. distance for parallel or offset pistacking (McGaughey, 1998)
PISTACK_ANG_DEV = 30  # Max. Deviation from parallel or perpendicular orientation (in degrees)
PISTACK_OFFSET_MAX = 2.0  # Maximum offset of the two rings (corresponds to the radius of benzene + 0.5 A)
PICATION_DIST_MAX = 6.0  # Max. distance between charged atom and aromatic ring center (Gallivan and Dougherty, 1999)
SALTBRIDGE_DIST_MAX = 4.0 #5.5  # Max. distance between centers of charge for salt bridges (Barlow and Thornton, 1983) + 1.5
HALOGEN_DIST_MAX = 4.0  # Max. distance between oxy. and halogen (Halogen bonds in biological molecules., Auffinger)+0.5
HALOGEN_ACC_ANGLE = 120  # Optimal acceptor angle (Halogen bonds in biological molecules., Auffinger)
HALOGEN_DON_ANGLE = 165  # Optimal donor angle (Halogen bonds in biological molecules., Auffinger)
HALOGEN_ANGLE_DEV = 30  # Max. deviation from optimal angle
WATER_BRIDGE_MINDIST = 2.5  # Min. distance between water oxygen and polar atom (Jiang et al., 2005) -0.1
WATER_BRIDGE_MAXDIST = 4.1  # Max. distance between water oxygen and polar atom (Jiang et al., 2005) +0.5
WATER_BRIDGE_OMEGA_MIN = 71  # Min. angle between acceptor, water oxygen and donor hydrogen (Jiang et al., 2005) - 9
WATER_BRIDGE_OMEGA_MAX = 140  # Max. angle between acceptor, water oxygen and donor hydrogen (Jiang et al., 2005)
WATER_BRIDGE_THETA_MIN = 100  # Min. angle between water oxygen, donor hydrogen and donor atom (Jiang et al., 2005)
METAL_DIST_MAX = 3.0  # Max. distance between metal ion and interacting atom (Harding, 2001)
~~~
<p style="font-size:12px;color:darkgrey" class="text-center">*Config.py file form an old PLIP version (1.4.4) with thresholds modifiations*</p>

From version 1.4.4/1.4.5 (the latest version until pharmAI started to maintain the code) to version 2.1.3 (july 2020) and to version 2.2.0 (actual) several changes have been performed, as can be seen in the [changelog](https://github.com/pharmai/plip/blob/master/CHANGES.txt). The evolution is specially notable if you compare with the first versions. Now PLIP is an even stronger interaction profiler that can handle not only protein-ligand interactions. Now protein-peptide interactions, DNA/RNA-ligand interactions and interactions within one chain can be detected. Moreover you can analyze different complexes in batch mode.

Probably what I missed now is the possibility of upload a full MD trajectory file. However there are ways to handle it like upload the trajectory with [mdtraj](https://www.mdtraj.org/1.9.5/index.html), [pytraj](https://amber-md.github.io/pytraj/latest/index.html) or [parmed](https://parmed.github.io/ParmEd/html/index.html), for example, extract PDB files from the different frames and then analyze them with PLIP. Other thing I would change is that the parsable txt files you can get as output, could be somehow csv files. This will simplify the automatic extraction/analysis of the diverse interactions, although it is not something too much complicated or time consuming. For few PDB files is fine to look at the report.txt files, but if you want to go further you need to automatize the process. For instance to filter out the compounds that perform an specific interaction from a virtual screening (docking based) using a database with thousands of compounds or if you want to check during how many frames in an MD simulation a certain interaction is established, you need to automatize the interactions extraction and filtering.

~~~html
traj=pt.iterload('/PATH/to/the/MD/target_ligand_solvent-w-MD.dcd', \
top='/PATH/to/the/topology/file/\
target_ligand_solvent.prmtop', frame_slice=[(0, 100, 10),])
traj=traj.strip(':WAT,:Na+')

count=0
for frame in traj:
    count=count+1
    pt.write_traj('trajectory_frame'+str(count)+'.pdb', traj=traj, overwrite=True)
    pt.write_traj('trajectory.pdb', traj=traj, overwrite=True)
    plip=('plipcmd -f ' + trajectory_frame'+str(count)+'.pdb -t')
    run_command(plip)
~~~
<p style="font-size:12px;color:darkgrey" class="text-center">*Analyze interactions of diverse frames from a NAMD trajectory with Pytraj and PLIP. Full sctipt can be found [here](https://github.com/MelchorSanchez/blog_post_example_scripts/blob/main/md_analysis_plip.py) *</p>

~~~html


~~~
<p style="font-size:12px;color:darkgrey" class="text-center">*Example code for parsing a PLIP output txt file*</p>


For me PLIP is a must for a bioinfomatician/chemoinformatician/computational biologist/computational chemist (in another post we could talk about why the same thing can have a different name depending on your background). There are other protein-ligand interaction profilers out there, some of them with the capacity of generating 2D maps like the ones from Schrödinger suite, Discovery studio , Inteligand or the also open source LigPlot(+). But, in my humble opinion, none of them offers the flexibility of PLIP, as a consequence of be an open source python-based tool, and are not as complete as PLIP due to the high number of different interactions it can detects in different scenarios.

 For a full documentation of running options and output formats of PLIP, please refer to the [Documentation](https://github.com/pharmai/plip/blob/master/DOCUMENTATION.md).
