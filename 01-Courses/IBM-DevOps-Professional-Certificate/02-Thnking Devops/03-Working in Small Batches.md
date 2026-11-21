.Form Lean Manufacturing
. Faster feedback
. Supports experimentation
. Minimizes waste
. Deliver faster

Small  batch example
You need to mail 1000  brochures:
 . Step 1: Fold brochures
 . Step 2: Insert Brochures into envelopes
 . Step 3: Seal the envelopes
 . Step 4: Stamp the envelopes with postage
 
Batch of 50 brochures
Assume each step takes 6 seconds to complete (10/2)

```
> [!NOTE] Step 1: Fold (5 min) `[1]` `[1]` `[1]` `[1]` `[1]`

> [!TIP] Step 2: Insert (10 min) `[2]` `[2]` `[2]` `[2]` `[2]`

> [!WARNING] Step 3: Seal (15 min) `[3]` `[3]` `[3]` `[3]` `[3]`

> [!] step 4: stamp(16 min) '[4]''[4]''[4]''[4]''[4]''[4]''[4]' --> 1st Finshed product, 16 min
.What if the envelopes had no glue?
.what if there were a typo in the brochure?

```

Single Piece Flow
Assume each steps takes 6 seconds to complete

```
[1][2][3][4] --> [1][2][3][4] --> [1][2][3][4] --> [1][2][3][4]
```