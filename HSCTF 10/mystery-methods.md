<img width="308" alt="image" src="https://github.com/Jewber11/CTF-Writeups/assets/134816588/93d6ee19-45d8-4753-ab30-76ea12ba72a7">

This was a super fun rev challenge where you were given a java file with an encyption using three mystery methods: unknown, unknown1, and unknown2. Since this was a rev challenge, I started by trying to figure out what each of the 3 unknown methods did and then reversing them. Once I figured out what the three methods did, I just wrote a simple script that reversed the three methods:

```
import java.util.Base64;

public class Main {
    public static void main(String[] args) {
        String output = "OS1QYj9VaEolaDgTSTXxSWj5Uj5JNVwRUT4vX290L1ondF1z";

        // Reverse the transformations step by step
        StringBuilder step1 = new StringBuilder();
        for (char c : output.toCharArray()) {
            if (Character.isLetter(c)) {
                char base = Character.isUpperCase(c) ? 'A' : 'a';
                int offset = (c - base - 25) % 26;
                if (offset < 0) {
                    offset += 26;
                }
                c = (char) (base + offset);
            }
            step1.append(c);
        }

        byte[] decodedBytes = Base64.getDecoder().decode(step1.toString());
        String step2 = new String(decodedBytes);

        StringBuilder step3 = new StringBuilder(step2).reverse();
        String originalInput = step3.toString();

        System.out.println("Original Input: " + originalInput);
    }
}
```

Running this code outputted: "ZmxhZ3toc0NURl9JNV9yM2FMTHlfZlVOfQ==" which I then base64 decoded and got the flag: flag{hsCTF_I5_r3aLLy_fUN}
