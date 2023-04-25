---
title: De-Orphanizing Marine Molecules
subtitle: Computational Target Prediction
layout: post
group: blog
comments: true
author : Melchor Sanchez-Martinez
date: 2022-02-22
tags: [CADD, hit finding, in silico target prediction, target finding, target fishing, target profiling, virtual screening]
categories: [Computer Aided Drug Design, CADD, Cheminformatics, Structure Based Drug Design, SBDD, Target Prediction]
---
<!-- excerpt-start -->
Recently, in Burua Scientific we have published a new article highlighting the potentially **beneficial role of computer-aided drug design (CADD) techniques in marine drug discovery**. As we said in the [article](https://www.mdpi.com/1660-3397/20/1/53/htm), the oceans are an incredible source of bioactive compounds. But these compounds, once identified, are not easy to work with for a variety of reasons.

<img src="https://github.com/MelchorSanchez/MelchorSanchez.github.io/blob/master/static/img/blog/mardrugs2022-1024x1021.webp" alt="Target fishinf, Target finding, marine molecules">
<p style="font-size:12px;color:darkgrey" class="text-center"></p>

~~~html

metformin='CN(C)C(=N)NC(=N)N'
pk.read_from_smiles(metformin)
pk.optimize('HF/6-31g(d)')
respCharges=pk.calc_resp_charges()
res=defaultdict(list)
for i, atom in enumerate(pk.mol.GetAtoms()):
    res['SYMBOL'].append(atom.GetSymbol())
    res['RESP'].append(respCharges[i])
molecule_df = pd.DataFrame(res)

pk.read_from_molfile('metformin.mol')
pk.optimize('HF/6-31g(d)')
respCharges=pk.calc_resp_charges()
res=defaultdict(list)
for i, atom in enumerate(pk.mol.GetAtoms()):
    res['SYMBOL'].append(atom.GetSymbol())
    res['RESP'].append(respCharges[i])
molecule_df = pd.DataFrame(res)

~~~
<p style="font-size:12px;color:darkgrey" class="text-center">Example of RESP charges calculation starting from Smiles or a MOL file using Psikit. Code inspired by [Iwatobipen's blog post](https://iwatobipen.wordpress.com/2019/03/11/calculate-atomic-charges-with-psikit-rdkit-psi4/) </p>

Now we have more clear why RESP charges are interesting and how we can use it, but what can be the "real" applications of RESP charges? So for instance CADD projects. In a drug discovery project, the use of RESP charges cold be important, for example, to perform MD simulations of docking complexes with the aim of incorporating flexibility after rigid docking to test the stability of the complex and obtain a more accurate description of the binding mode due to the incorporation of the so-called induced fit events (more information on post-processing of docking poses with MD can be found [here](https://www.mdpi.com/1660-3397/15 / 12/366 / htm) or [here](https://onlinelibrary.wiley.com/doi/abs/10.1002/wcms.1320)) and / or to perform more accurate free (binding) energy calculations of the complex). In practice, what is done is to optimize the geometry of the docked molecule, calculate the RESP charges of the optimized conformation and add them together with the Cartesian coordinates, xyz, from the docking calculation, to a new SDF/MOL/MOL2 file. This file is input to antechamber. An interesting option would be to make antechamber recognize psi4 RESP calculation output, this will simplify the file manipulation, but by now I have not try it. Maybe it's already done and I am not aware of it. If it is the case, please let me know!

 So, let's try Psikit! Then add the RESP charges to you protein-ligand simulations and check if your results improve! [Here you can find an example that uses Psikit to calculate RESP charges that then are reflected into a parameterized file coming from antechamber that finally is converted to Gromacs topology](https://github.com/MelchorSanchez/blog_post_example_scripts/blob/main/resp_calculation.py).
