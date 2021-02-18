# Making MD movies in ChimeraX
ChimeraX doesn't allow you to load amber prmtops like Chimera. To get around this:

0. Open a pdb of the system you simulated (you can usually use the neutralized structure you made in prep). 
> `open <path to pdb>`
1. Remove any extra atoms that aren't in your trajectory file (i.e. you stripped the trajectory, so get rid of the waters and salts), make sure it is protonated if your trajectory is (you will get an error in the next step saying you have many less atoms than you need.
2. Load the trajectory into your pdb.
> `open <path to trajectory> structureModel #1`
3. Make it pretty.
> `set bgColor white; hide protein atoms; show nucleic cartoon; nucleotides ladder; color nucleic #aaaaaa; color protein #ffb347; lighting soft; graphics silhouettes width 1.5; nucleotides tube/slab shape box; view`
4. You can scroll through your trajectory.
> `coordset slider #1`
5. Record the movie (the wait 310 command will record 310 frames, which is 10 more than the trajectory file.
> `movie record; coordset #1 1,30000,100 holdSteady @ca; wait 310; movie encode D:/shawn/md_movies/0M_hpya_tetra_nuc_300ns.mp4`