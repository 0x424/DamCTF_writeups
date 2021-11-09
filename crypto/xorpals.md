One of the 60-character strings in the provided file has been encrypted by single-character XOR. The challenge is to find it, as that is the flag.
\
Hint: Always operate on raw bytes, never on encoded strings. Flag must be submitted as UTF8 string.
\
\
There are 98 lines in flags.txt, and one of them is a flag with xor encryption.
\
Brute-force these lines until string with 'dam' is found. (flag format: dam{flag})
\
\
\
<flags.txt>
045c3f704f355f6e70536d1e4246573c34096b022f1a077a1d2b676052275f493618787c5a250545254e12750c2261511e5c0d0045376722002a6602\
6c3c73194c4e3e3a0563684b600b5c7f1333044e622534244065241e1e0f5f515245546d2030455518065220006b0e3c4b621064732340721f332225\
31182e4e4f635b4d506c54282b764a6e70763f24755b1b694a2e0e2c070d0201397277511e72762b2f3a2037720b442e143f5b706f7602787c22643f\
52681b5d39262d102e420b42545a085f28581e401f6f657d2e0b5f35357b1569787572466b4f5b106a7975371f537a137c2b671e7972327d4d2b7f4a\
177e19705e55251f704e7632796e772728374a63382d5d314b390849747728496d09101458682a2e587400124845677e5d24174c1c0a64396e24091e\
000d781b6c4b5e6c6529353b785c31752b36421f482b477e300060622839776e193a3c7e10156c715f39534d184d0e363a1027014f2d27525c5e3175\
331a1d621e4765163e474245576455600d5c380c612d043d7f41175e682905797a0c2e7f2e2c5c203b6b2e0e21621014206e4b14154b5f1726034c77\
042f6e3b401675587240631b06631d5f0119251801413b354a4c40112a3c387c275f4a612a060208653a3d0c0c4908334918295015466c53020b2571\
...(90)
\
\
python code for brute-forcing:
\
f = open(f"flags.txt", 'r')\
lines = f.readlines()\
for line in lines:\
    b = bytes.fromhex(line)\
    for k in range(255):\
        d = bytes([b[i] ^ k for i in range(len(b))])\
        if d[:3] == b'dam':\
            print(d)\
            break\
\
\
\
flag:
\
dam{antman_EXPANDS_inside_tHaNoS_never_sinGLE_cHaR_xOr_yeet}
\
\
\
