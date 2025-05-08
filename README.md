# EX-NO-10-Diffie-Hellman-Key-Exchange-Algorithm

## AIM:
To Implement Diffie Hellman Key Exchange Algorithm 

## Algorithm:

1. Diffie-Hellman Key Exchange is used for securely sharing a secret key between two parties over an insecure channel.

2. Initialization: Agree on a large prime number \( p \) and a primitive root \( g \) modulo \( p \) (both are public values).

3. Key Exchange Process: 
   - Each party selects a private key and calculates their public key using the formula \( g^{\text{private key}} \mod p \).
   - Each party then shares their public key with the other.

4. Secret Key Computation: 
   - Each party computes the shared secret key using the received public key and their own private key.

5. Security: The difficulty of computing discrete logarithms ensures that the shared key remains secure even if public values are intercepted.

## Program:
```
#include <stdio.h>
#include <math.h>

// Function to perform modular exponentiation
long long power(long long base, long long exponent, long long mod) {
    long long result = 1;
    base = base % mod;

    while (exponent > 0) {
        if (exponent % 2 == 1)  // If exponent is odd
            result = (result * base) % mod;
        exponent = exponent >> 1;  // Divide by 2
        base = (base * base) % mod;
    }
    return result;
}

int main() {
    long long p, g, privateA, privateB, publicA, publicB, secretA, secretB;

    printf("Enter a prime number (p): ");
    scanf("%lld", &p);

    printf("Enter a primitive root of p (g): ");
    scanf("%lld", &g);

    printf("Enter private key for User A: ");
    scanf("%lld", &privateA);

    printf("Enter private key for User B: ");
    scanf("%lld", &privateB);

    // Generate public keys
    publicA = power(g, privateA, p);
    publicB = power(g, privateB, p);

    printf("\nPublic key of A: %lld", publicA);
    printf("\nPublic key of B: %lld", publicB);

    // Generate shared secret keys
    secretA = power(publicB, privateA, p); // A computes secret
    secretB = power(publicA, privateB, p); // B computes secret

    printf("\n\nShared Secret Key computed by A: %lld", secretA);
    printf("\nShared Secret Key computed by B: %lld\n", secretB);

    if (secretA == secretB) {
        printf("\n✅ Key exchange successful. Both users share the same secret key.\n");
    } else {
        printf("\n❌ Key mismatch. Something went wrong.\n");
    }

    return 0;
}
```


## Output:

![image](https://github.com/user-attachments/assets/174b520c-6f7e-4a96-bd69-1646d09828ba)


## Result:
  The program is executed successfully

