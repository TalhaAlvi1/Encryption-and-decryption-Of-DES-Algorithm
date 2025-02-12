# Objective
The objective of the Data Encryption Standard (DES) algorithm is to provide secure data encryption through symmetric-key cryptography. DES encrypts data in 64-bit blocks using a 56-bit key, transforming plaintext into ciphertext through a series of permutations and substitutions. This process helps protect sensitive information by making it unintelligible to unauthorized parties. DES ensures data integrity and confidentiality by enabling both encryption and decryption, allowing only authorized users with the correct key to access the original information.
# Algorithm

**Key Generation and Scheduling:**

1.Generate a 56-bit key, then expand it to 64 bits by adding parity bits.

2.Create 16 subkeys of 48 bits each, used in each encryption round. These subkeys are derived by shifting and permutating the original key.

**Initial Permutation (IP):**

Perform an initial permutation on the 64-bit plaintext block. This rearranges the bits according to a predefined table and sets up the block for the rounds of processing.

**Splitting the Block:**

Divide the permuted block into two 32-bit halves, named the Left (L) and Right (R) halves.

**Rounds of Processing (16 Rounds):**

For each of the 16 rounds, repeat the following steps:

**1.Expansion (E):** Expand the 32-bit R half to 48 bits by duplicating and rearranging bits, preparing it for the XOR operation with the subkey.

**2.Key Mixing:** XOR the expanded R half with the 48-bit subkey for the current round.

**3.Substitution (S-Boxes):** Divide the XOR result into 8 blocks of 6 bits each and pass each through a unique substitution box (S-box), converting each 6-bit input into a 4-bit output.

**4.Permutation (P):** Permute the 32-bit output from the S-boxes according to a predefined table.

**5.Swapping:** XOR this 32-bit output with the current L half and swap L and R. The new R becomes the output from the XOR, and L takes on the previous R value.

**Final Permutation (IP-1):**
After the 16th round, combine the L and R halves and apply the inverse of the initial permutation to get the final 64-bit ciphertext.

**Decryption:**
For decryption, repeat the same steps but apply the subkeys in reverse order, effectively reversing the encryption process and recovering the original plaintext.

# Explanation:
DES operates on blocks of data (64 bits at a time) and uses a key of 56 bits for encryption and decryption. The algorithm is based on a Feistel network, a structure that divides the block into two halves and applies multiple rounds of transformations.

**Key Structure**

The key used in DES is 64 bits long, but only 56 bits are used for actual encryption. The remaining 8 bits are used for parity checking.

The key undergoes permutation and splitting before being used for encryption.

**DES Encryption Process**

The DES encryption process can be broken down into several key steps:

Step 1: **Initial Permutation (IP)**

The 64-bit input block undergoes an initial permutation, which rearranges the order of the bits. This is not a cryptographic step but helps to ensure that the encryption is more secure by altering the structure of the data.

Step 2: **Key Scheduling**

The 56-bit key is split into two 28-bit halves. Each half is then rotated and subjected to a permutation at each of the 16 rounds, creating 16 different subkeys (one for each round).

Step 3: **Rounds (16 Rounds in Total)**

The 64-bit data block is processed in 16 rounds, where each round applies a series of transformations. In each round, the data block is divided into two halves:

Left half (L): 32 bits

Right half (R): 32 bits

The operations performed in each round are as follows:

**Expansion (E):** The 32-bit right half is expanded to 48 bits using a fixed expansion permutation (E-box).

**Subkey XOR:** The expanded right half is XORed with the round-specific subkey (generated from the original 56-bit key).

**Substitution (S-Boxes):** The resulting 48-bit value is split into eight 6-bit chunks. Each chunk is passed through a substitution box (S-box), which reduces it to a 4-bit value. There are 8 S-boxes in DES, and each S-box is designed to provide non-linear substitution to enhance security.

**Permutation (P):** The 32-bit result from the S-boxes is permuted using a fixed permutation (P-box) to produce a 32-bit value.

**XOR with Left Half:** The result is then XORed with the left half of the data block. The right half becomes the new left half for the next round, while the result of the XOR operation becomes the new right half.

This process is repeated for 16 rounds, with the left and right halves being updated each time. After the 16th round, the final left and right halves are combined to form a 64-bit output block.

Step 4: **Final Permutation (FP)**

After all 16 rounds, the 64-bit block is subjected to a final permutation, which is the inverse of the initial permutation (IP). This results in the final encrypted ciphertext.
