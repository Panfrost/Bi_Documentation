
# General purpose registers
The ISA seems to allow you to encode up to 64 registers in to it. Some of the higher registers seem to be special case uses that aren't fully explored
* Registers can be viewed as different types depending on instruction encoding
** Rn
** Sn
** Dn
** Qn
** vector type?
```
Dn, QUIn, On, SEPn, Qn, Rn, Sn, Tn, where n is a number
```

# Temporary registers
The ISA has the concept of a temporary register. According to an architecture dive, it seems these allow instructions in a bundle to pass a result directly from one instruction to the next instruction in the same clause bundle
* The hardware seems to support 8 temporary registers
* Overview implies that this temporary can only be passed between instructions in the same clause
** Maybe some clause header/tail flags let you pass them between clauses
* The temporary only lasts between one instruction and the next
* It is invalid to have a instruction inbetween the one that writes to it, and the one that reads to it.
** Probably only retains itself for a single instruction in the pipeline before it flushes to the pipeline register file
** Doesn't explain how eight of these are supposed to work

# Uniform/Constant registers
The Hardware exposes 1024 uniform registers. These registers seem to be allowed to encode directly in the instruction encoding.
1024 registers would require 10bits to encode all of them.
* Can uniform constants be on both inputs of an instruction?
** Adreno for example only allows one input to be from a constant register.
