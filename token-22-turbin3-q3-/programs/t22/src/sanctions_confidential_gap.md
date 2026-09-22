# Sanctions and Confidential Balances

If a sanctioned holder moves tokens from the public balance into the
confidential balance before the permanent delegate acts, the issuer has a real
enforcement gap.

The permanent delegate can seize ordinary public token balances with a normal
Token-2022 transfer, because the token program recognizes the permanent
delegate as an authority for non-confidential transfers and burns. That does
not give the delegate the holder's confidential keys.

Confidential transfer and withdrawal require proofs built from the holder's
current encrypted balance and a new decryptable balance encrypted under the
holder's AES key. The permanent delegate can see that the account has a
confidential extension, but it cannot decrypt the balance, compute the new
decryptable balance, or generate the owner's transfer/withdraw proof.

So the issuer can still freeze the account and block future movement, and it
can seize any remaining public balance. But funds already moved into the
confidential available or pending balance are not practically seizable by the
permanent delegate alone. The design needs an additional compliance mechanism,
such as an auditor/recovery key or a policy that blocks confidential deposits
for accounts under review before sanctions are applied.
