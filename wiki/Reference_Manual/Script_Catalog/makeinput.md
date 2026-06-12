# makeinput
> ### makeinput is the main script for input preperation. Reads an olcao.skl file in the current directory and generates all the inputs for uolcao

USAGE: makeinput [-basisdb \$atomicBDB] [-potdb \$atomicPDB]
                 [-modpot \$modElementName \$minModTerm \$maxModTerm
                          \$numModTerms]
                 [-subbasis \$basisSubOut \$basisSubIn [-subbasis ...]]
                 [-subpot \$potSubOut \$potSubIn [-subpot ...]]
                 [[[-scfkp \$a \$b \$c] [-pscfkp \$a \$b \$c]
                   | [-kp \$a \$b \$c]]
                 [-kpshift \$a \$b \$c]
                 [-printbz \$bz \$scaleFactor]
                 [-xccode \$xcCode]
                 [-xcmesh [-numvect \$numSampVectors]
                          [-weight \$xcInWeight \$xcOutWeight]
                          [-samp \$xcInSamp \$xcOutSamp \$xcSpacingSamp]]
                 [-target <[-atom \$targetAtom] || [-atxyz \$x \$y \$z] ||
                           [-atabc \$a \$b \$c]> [-sphere \$targetRadius]
                           [-zone \$targetZone] [-operand \$targetOp]
                           [-relate \$targetRelation]]
                 [-block <-abc \$froma \$toa \$fromb \$tob \$fromz \$toc>
                         [-zone \$blockZone] [-operand \$blockOp]
                         [-relate \$blockRelation]]
                 [-reduce [-level \$reduceLevel] [-thick \$reduceThick]
                          [-cutoff \$reduceCutoff] [-operand \$reduceOp]
                          [-tolerance \$reduceTolerance]
                          [-selection \$reduceSelection]]
                 [-xanes [-sphere \$xanesRadius]
                         [-atom \$xanesAtom1 [\$xanesAtom2 [...]]]]
                 [-sybdpath \$sybdPath]
                 [-rel]
                 [-statefactor \$factor]
                 [-pdb] [-cif] [-basisVis]
                 [-emu]
                 [-nocore]
                 [-slurm [-p \$partition] [-a \$account] [-t \$time]
                         [-m \$memory] [-n \$cpus] [-N \$nodes]]
                 [-help]


