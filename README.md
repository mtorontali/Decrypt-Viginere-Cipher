# Decrypt Vigenere Cipher
A java program that decrypts a vigenere cipher ciphertext by checking keys from a list of 1000 most common english words.

```java
// Matthew Torontali
// 9/10/2020
// Decrypt vigenere cipher text without knowing the key, we do know that the key is from the list of 1000 most common
// english words.
// Some code and ideas used from Arup Guha's h2q4.java file found here:
// http://www.cs.ucf.edu/courses/cis3362/fall2019/hmk/h2/h2q4.java

import java.util.*;
import java.io.*;

public class decryptVigenere
{

	public static void main(String[] args) throws Exception
	{
	
		// Initialize scanner to take input
		Scanner scanner = new Scanner(System.in);

		// Ask user for input
		System.out.println("Enter cipher text to be decrypted: ");

		// Initialize cipherText variable and set it to next input
		String cipherText = scanner.next();

		// Take in all of the possible 1000 keys from this list
		Scanner possibleKeys = new Scanner(new FileReader("possibleKeys.txt"));

		// Try each possible key with the decryption alogrithm to see if the plaintext contains "mate"
		// Modified some code found in Arup Guha's h2q4.java
		while (possibleKeys.hasNext())
		{

			String possibleKey = possibleKeys.next();
			String plainText = decrypt(cipherText, possibleKey);

			// Print decrypted plaintext
			if (plainText.contains("mate"))
			{
				System.out.println("The decrypted plaintext is: ");
				System.out.println(plainText);
				System.out.println("The key used to decrypt: ");
				System.out.println(possibleKey);
			}
		}
	}

	// This function was written by Arup Guha
	// Returns the decryption of ciphertext cipher with key using the Vigenere cipher.
	public static String decrypt(String cipher, String key)
	{
		char[] res = new char[cipher.length()];
		
		// Just sub out each appropriate letter
		for (int i=0; i<res.length; i++)
			res[i] = (char)((cipher.charAt(i) - key.charAt(i%key.length()) + 26)%26 + 'a');
		return new String(res);
	
	}
}
```