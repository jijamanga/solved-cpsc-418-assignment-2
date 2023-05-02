Download Link: https://assignmentchef.com/product/solved-cpsc-418-assignment-2
<br>
Problem 1 — Arithmetic in the AES MixColumns operation (20 marks)

Recall that the MixColumns operation in AES performs arithmetic on 4-byte vectors using the polynomial M(y) = y<sup>4</sup> + 1. In this arithmetic, we have M(y) = 0, so y<sup>4</sup> = 1.

<ol>

 <li>In this part of the problem, we consider multiplication of 4-byte vectors (viewed as polynomials of degree ≤ 3 whose coefficients are bytes) by powers of y.</li>

</ol>

<ul>

 <li>(2 marks) Formally prove that in this arithmetic, multiplication of any 4-byte vector by y is a circular left shift of the vector by one byte.</li>

 <li>(4 marks) Generalizing part (i) to other powers of y, formally prove that multiplication of any 4-byte vector by y<sup>i</sup> (0 ≤ i ≤ 3) is a circular left shift of the vector by i</li>

</ul>

<ol>

 <li>Next, we consider arithmetic involving the coefficients of the polynomial</li>

</ol>

c(y) = (03)y<sup>3</sup> + (01)y<sup>2</sup> + (01)y + (02) ,

that appears in MixColumns, where the coefficients of c(y) are bytes written in hexadecimal (i.e. base 16) notation. Arithmetic involving this polynomial requires the computation of prod­ucts involving the bytes (01), (02) and (03) in the Rijndahl field GF(2<sup>8</sup>). Recall that in this field, arithmetic is done modulo m(x) = x<sup>8</sup> + x<sup>4</sup> + x<sup>3</sup> + x + 1.

<ul>

 <li>(2 marks) Write the bytes (01), (02), (03) as their respective polynomial representatives c1(x), c2(x) and c3(x) in the Rijndahl field GF(2<sup>8</sup>).</li>

 <li>(4 marks) Let b = (b7 b6 · · b1 b0) be any byte, and let d = (02)b be the product of the bytes (02) and b in the Rijndahl field GF(2<sup>8</sup>). Then d is again a byte of the form d = (d7 d6 · · · d1 d0). Provide formulas for the bits di, 0 ≤ i ≤ 7, in terms of the bits bi.</li>

 <li>(3 marks) Provide analogous expressions as in part (b) (ii) for the byte product e = (03)b, where b = (b7 b6 · · b1 b0) is any byte.</li>

</ul>

<ol>

 <li>The MixColumns operation performs multiplication of 4-byte vectors by the polynomial c(y) of part (b). In this part of the problem, you will evaluate such products symbolically.</li>

</ol>

<ul>

 <li>(3 marks) Let s(y) = s3y<sup>3</sup> + s2y<sup>2</sup> + s1y + s0 be a polynomial whose coefficients are bytes. Symbolically compute the product t(y) = s(y)c(y) mod y<sup>4</sup> + 1. The result should be a polynomial of the form t(y) = t3y<sup>3</sup> + t2y<sup>2</sup> + t1y + t0 where t3, t2, t1, t0 are bytes. Provide formulas for the bytes ti, 0 ≤ i ≤ 3, in terms of the bytes si. The equations should consist of sums of byte products of the form 01si, 02si, 03si, 0 ≤ i ≤ You need not compute these individual byte products as you did in part (b).</li>

 <li>(2 marks) Write your solution of part (c) (i) in matrix form; i.e. give a 4 × 4 matrix C whose entries are bytes such that</li>

</ul>

t0t1

t2

t3

Note that this yields the matrix representation of MixColumns presented (without proof) in class.




Problem 2 Error propagation in block cipher modes (12 marks)

Error propagation is often an important consideration when choosing a mode of operation in prac­tice. In this problem, you will analyze the error propagation properties of an arbitrary block cipher in various such modes; note that these properties are independent of the cipher used.

<ol>

 <li>Suppose Alice wants to send a sequence of message blocks M0, M1, M2,… to Bob, encrypted to ciphertext blocks C0, C1, C2,… using some fixed key K. Assume that an error occurs during transmission of a particular block of ciphertext Ci. Justifying all your answers, explain which plaintext blocks are affected after Bob decrypts this (faulty) ciphertext block Ci when the cipher is used in</li>

</ol>

<ul>

 <li>(2 marks) ECB mode?</li>

 <li>(2 marks) CBC mode?</li>

 <li>(2 marks) OFB mode?</li>

 <li>(2 marks) CFB mode with one register?</li>

 <li>(2 marks) CTR mode?</li>

</ul>

<ol>

 <li>(2 marks) Suppose now that an error occurs in a particular plaintext block Mi before Alice encrypts it and sends the corresponding ciphertext Ci to Bob. Upon decryption of Ci, which plaintext blocks Mj are affected when using the cipher in CBC mode?</li>

</ol>

Problem 3 Binary exponentiation (13 marks)

Recall the exponentiation algorithm given in class for evaluating a<sup>n</sup> (mod m) (a E Z, m, n E N):

<ol>

 <li>Compute the binary representation of n:</li>

</ol>

n = b02<sup>k</sup> + b12<sup>k_1</sup> + + bk_12 + bk ,

with b0 = 1, bi E {0, 11 for 1 &lt; i &lt; k, and k = Llog<sub>2</sub> n].

<ol start="2">

 <li>Initialize r0 a (mod m). ~</li>

</ol>

r<sup>2</sup><sub>i</sub> (mod m)         if bi+1 = 0 ,

<ol start="3">

 <li>For 0 &lt; i &lt; k – 1 compute ri+1 = r<sup>2</sup><sub>i</sub> a (mod m) if bi+1 = 1 .</li>

 <li>Output rk.</li>

 <li>(3 marks) To warm up with a toy example, compute<sup> 1711</sup> (mod 77) using the procedure above; answers that don’t use the binary exponentiation algorithm will receive no credit, even if they are correct. Show all your work, and write down all your intermediate quantities bi and ri. Your answer should be an integer between 0 and 76.</li>

 <li>In this problem, you will formally prove that the binary exponentiation algorithm is correct. (i) (4 marks) Define s0 = 1 and si+1 = 2si + bi+1 for 0 &lt; i &lt; k – Use induction on i to prove that</li>

</ol>

i

bj2<sup>i_j</sup> for 0 &lt; i &lt; k .




<ul>

 <li>(4 marks) Let ri, 0 ≤ i ≤ k, be defined as in steps 2 and 3 of the exponentiation algorithm. Use induction on i to prove that ri ≡ a<sup>s</sup> (mod m) for 0 ≤ i ≤ k.</li>

 <li>(2 marks) Prove that a<sup>n</sup> ≡ rk (mod m), so the algorithm above does indeed compute an (mod m) as claimed.</li>

</ul>

Problem 4 A modified man-in-the-middle attack on Diffie-Hellman (10 marks)

Suppose Alice and Bob wish to generate a shared cryptographic key using the Diffie-Hellman protocol. As usual, they agree on a large prime p and a primitive root g of p. Suppose also that p = mq + 1 where q is prime and m is very small (so p − 1 = mq has a large prime factor, as is generally required). Since g and p are public, it is easy for anyone to deduce m and q; for example by successively trial-dividing p − 1 by m = 2,4,6,… and running a primality test such as the Fermat test on the quotient q = (p − 1)/m until primality of q is established.

Suppose an active attacker Mallory<sup>1</sup> intercepts g<sup>a</sup> (mod p) from Alice and g<sup>b</sup> (mod p) from Bob. She sends (g<sup>a</sup>)q (mod p) to Bob and (g<sup>b</sup>)q (mod p) to Alice.

<ol>

 <li>(2 marks) Show that Alice and Bob compute the same shared key K under this attack.</li>

 <li>(4 marks) Show that there are m possible values for K, and that Mallory can compute them all and hence easily guess the correct key K among them.</li>

 <li>(4 marks) What is the advantage of this variation of the man-in-the-middle attack over the version we discussed in class? Recall that for the attack from class, Mallory simply suppresses the messages g<sup>a</sup> (mod p) and g<sup>b</sup> (mod p) between Alice and Bob and replaces them with her own number g<sup>e</sup> (mod p), which results in the shared key g<sup>ae</sup> (mod p) between Mallory and Alice and the shared key g be (mod p) between Mallory and Bob.</li>

</ol>

Problem 5            A simplified password-based key agreement protocol (8 marks)

The following is a simplified (and hence problematic) version of the key generation phase of the password-based key agreement protocol that you are being asked to implement in Problem 9 (the programming problem). Here, a client first performs a one-time registration of their authentication credentials with a server. These credentials can then be used to generate authenticated session keys between server and client via communication over an insecure channel.

All participants agree on a large public prime<sup>2</sup> N = 2q + 1, with q prime, and a public primitive root g of N. Each client has their own password p. To register with the server, a client computes v ≡ gp (mod N) and provides the server with the pair (I, v) where I is the client’s user id.<sup>3</sup>

Protocol:

<ol>

 <li>Client generates a random value a with 0 ≤ a ≤ N − 1, computes A ≡ g<sup>a</sup> (mod N), and sends (I, A) to server, where I is the Client’s user id.</li>

</ol>

<sup>1</sup>This is a standard name for active attackers and is meant to be reminiscent of the word “malicious”. <sup>2</sup>We denote this prime by N, rather than p, because the letter p is reserved for the client’s password. <sup>3</sup>In practice, this needs to be done in a secure and tamper-proof manner. Also, in the computation of v, the client

would use a hash of their password p rather than just p. For details, see the protocol description in Problem 9.




Server generates a random value b with 0 b N – 1, computes B g<sup>b</sup> (mod N), and sends B to client.

<ol start="2">

 <li>Client computes Kclient Ba+p (mod N).</li>

</ol>

Server retrieves client’s authentication data (I, v) and computes <sub>K</sub><sub>server</sub> (Av)<sup>b</sup> (mod N).

Note that this protocol is similar to Diffie-Hellman, except that the client’s password p and au­thentication credential v are incorporated in the key computation.

<ol>

 <li>[2 marks] Prove that Client and Server have a shared key after executing this protocol, i.e. prove that Kserver = Kclient.</li>

 <li>[3 marks] Suppose an adversary Mallory obtains client Ian’s authentication data (I, v) (by intercepting Ian’s transmission to the server upon his registration or by hacking into the server’s database). Show how Mallory can masquerade as Ian, i.e. execute the protocol with the server (using a value A of her choice) and generate a valid key <sub>K</sub><sub>client</sub> that the server believes is shared with Ian.</li>

 <li>[3 marks] Consider the following two problems:</li>

</ol>

<ul>

 <li>Key Recovery Problem: Given any values A g<sup>a</sup> (mod N) and B g<sup>b</sup> (mod N) and any v E Z<sup>∗</sup><sub> N</sub>, find a key K produced by the protocol above.</li>

 <li>Diffie-Hellman Problem: Given any values A g<sup>a</sup> (mod N) and B g<sup>b</sup> (mod N), find a Diffie-Hellman key K g<sup>ab</sup> (mod N).</li>

</ul>

Note that the exponents a and b are assumed to be unknown for both these problems. Show how an attacker Mallory who can solve any instance of the key recovery problem can solve any instance of the Diffie-Hellman problem. (So informally, breaking the key agreement protocol above is at least as hard as breaking Diffie-Hellman.)

Written Problems for MATH 318 only

Problem 6 — Discrete logs with respect to different primitive roots (6 marks)

Let p be a prime and g a primitive root of p. Recall that for any a E Z<sup>∗</sup><sub> p</sub>, the discrete logarithm of a with respect to g is unique integer x with 0 x p – 2 and g<sup>x</sup> ~ a (mod p).

Recall that the discrete problem is asserted to be computationally intractable. This raises the natural question of whether this problem might be easier to solve for some primitive roots than for others. In this problem you will prove that that the difficulty of the discrete logarithm problem is independent of the choice of primitive root.

Specifically, let g, h be primitive roots of p and assume that for any element in Z<sup>∗</sup><sub> p</sub>, computing its discrete logarithm with respect to g is easy. Give an algorithm for easily computing its discrete logarithm with respect to h.




Let q ≥ 3 be a prime such that p = 2q+1 is also prime. Let g be any primitive root of p. Prove that with the exception of gq (mod p), all the odd powers of g (i.e. g, g<sup>3</sup> (mod p), g<sup>5</sup> (mod p),… , gp−2 (mod p)), are primitive roots of p.

(Hint: the following fact about divisibility, which you may use without proof, might come in handy: for any three nonzero integers a, b, c, if a is a divisor of the product bc and gcd(a, b) = 1, then a is a divisor of c.)

Problem 8            An algorithm for extracting discrete logarithms (25 marks)

Let p be a large prime and g a fixed primitive root of p. Let h ∈ Z∗ p be the modular inverse of g, so gh ≡ 1 (mod p). Let a ∈ Z<sup>∗</sup><sub> p</sub>. Define the following lists of elements in Z<sup>∗</sup><sub> p</sub>:

yi ≡ ah<sup>i</sup> (mod p), 0 ≤ i ≤ m − 1; zj ≡ (g<sup>m</sup>)j (mod p), 0 ≤ j ≤ k − 1.

Here, m is a positive integer (an as yet unspecified parameter) and k is the smallest integer with k ≥ (p − 1)/m, so k ≥ (p − 1)/m &gt; k − 1.

<ol>

 <li>(4 marks) Prove that there exist indices i, j with 0 ≤ i ≤ m − 1 and 0 ≤ j ≤ k − 1 such that yi = zj.</li>

</ol>

(Hint: Division with remainder of x by m where x is the (unknown) discrete logarithm of a with respect to g.)

<ol>

 <li>(5 marks) Consider the following procedure for computing the discrete logarithm of a with respect to g.</li>

 <li>Compute the listY = (y0,y1,.. . ,ym−1)</li>

 <li>If yi ≡ 1 (mod p) for some i ∈ {0, 1,. . . , m − 1}, then output i and quit.</li>

 <li>Compute the list Z = (z0, z1, z2,…, ) until an element zj is found that appears in Y.</li>

 <li>Upon finding such a match, say zj = yi, output x ≡ jm + i (mod p − 1). Prove that this procedure terminates and outputs the discrete logarithm of a.</li>

 <li>(4 marks) The computational cost of this algorithm is determined by the number of modular multiplications required to generate the lists Y and Z (we may ignore the cost of step 2 and of searching the list Y for a match to an element in Z in step 3 as these tasks take negligible time).</li>

</ol>

Assume the worst case scenario where the entire list Z = (z0, z1,.. . , <sub>z</sub><sub>k−1)</sub> needs to be generated before a match with an element in the list Y is found. How many modular multiplications are required to extract the discrete logarithm of a using the procedure above? Your count should be as accurate as possible (i.e. don’t count modular multiplications that aren’t needed). You may assume that k and g<sup>m</sup> (mod p) have been precomputed as they are independent of a.




<ol>

 <li>(5 marks) How should m be chosen to minimize the number of modular multiplication deter­mined in part (c)? Explain your choice.</li>

</ol>

(Hint: Your answer should be a function of p that’s close to √p.)

<ol start="107">

 <li>Let p = 107.</li>

</ol>

<ul>

 <li>(2 marks) Use the primitive root test from class to verify that 2 is a primitive root of p. Show your work.</li>

 <li>(4 marks) Use the procedure from part (b) and your choice of m from part (d) to compute the discrete logarithm of 6 with respect to 2 in Z∗ 107. Show your work. You may want to verify that your final answer is correct.</li>

</ul>

Programming Problem for CPSC 418 only

Problem 9 — Secure password based authentication and key exchange (37 marks)

Overview. This problem considers the full, secure version of the password-based key agreement protocol introduced in Problem 5. This protocol, executed by a Client and a Server, allows the Client to demonstrate to the Server knowledge of a password, but neither the password nor any other information that could be used to derive the password need to be transmitted. Additionally, the Server does not store password-equivalent data, so someone who intercepts authentication data or steals them from the Server’s database is unable to masquerade as the Client without brute-forcing the Client’s password.

To execute the protocol, there is an initialization and registration phase between the Client and Server. Doing this securely is in itself a complex problem, and so we instead perform a simplified version as described below.

The Server initializes in the following manner:

<ol>

 <li>Generates a 512-bit safe prime N by first generating a random 511-bit prime q and checking whether N = 2q + 1 is prime. Repeat until a valid N is found.</li>

 <li>Finds a primitive root g of N, which may be up to 512 bits in size.</li>

 <li>Computes the quantity k = H(N g), where ‘ ’ denotes concatenation and H is a cryptograph­ically secure hash function.</li>

 <li>Opens a socket connection on a specified IP and port and attempts to receive a single byte, whose value indicates the Server response. This byte is limited to the UTF-8 encoding of the characters ‘r’ indicating Client wishes to initiate registration; ‘p’ indicating the Client wishes to initiate the protocol; and ‘q’ indicating the Client wishes the Server to shut down.<sup>4</sup></li>

</ol>

The Server performs registration as follows:

<ol>

 <li>Server sends the values N,g to the Client.</li>

 <li>Server receives a single byte containing the length of the Client’s username, followed by username, s, v. Server stores these values.</li>

 <li>Server resumes listening on the socket, for another command.</li>

</ol>

<sup>4</sup><sup>A</sup> true implementation would not have this last feature, but it makes debugging much easier.




The Client performs registration as follows:

<ol>

 <li>The username username and a password pw are retrieved from the command line.<sup>5</sup></li>

 <li>Generates a random 16-byte salt<sup>6</sup> s.</li>

 <li>Connect to the Server’s socket and sends a one-byte character ‘r’;</li>

 <li>Receives the values N, g;</li>

 <li>Computes x = H(s||pw) and v ≡ g<sup>x</sup> (mod N);</li>

 <li>Computes and sends a single byte containing the byte-length of username, followed by username encoded in UTF-8, s, and v.</li>

</ol>

In a similar manner, if a Client connects to the Server and wishes to initiate the protocol, they willfirst send a single byte corresponding to ‘p’ before commencing with the protocol described below.

Protocol.

To generate and verify a shared authenticated session key, the Server and Client perform the following steps:

<ol>

 <li>Client generates a random value a with 0 ≤ a ≤ N − 1, computes A ≡ g<sup>a</sup> (mod N), and sends the length of the username as a single byte, followed by username, A.</li>

</ol>

Server generates a random value b with 0 ≤ b ≤ N − 1, computes B ≡ kv + g<sup>b</sup> (mod N), and sends s, B, where s is the Client’s salt.

<ol start="2">

 <li>Client and Server compute u ≡ H(A||B) (mod N).</li>

 <li>Client computes Kclient ≡ (B − kv)<sup>a+ux</sup> (mod N).</li>

</ol>

Server computes Kserver ≡ (Av<sup>u</sup>)<sup>b</sup> (mod N).

<ol start="4">

 <li>Client computes and sends M1 = H(A||B||Kclient).</li>

 <li>Server computes <sub>H</sub><sub>(</sub><sub>A||B||K</sub><sub>server</sub><sub>)</sub> and compares the result to M1. If they do not match, the authentication has failed and the socket is closed.</li>

 <li>Server computes and sends M2 = H(A||M1||Kserver).</li>

 <li>Client computes <sub>H</sub><sub>(</sub><sub>A||M</sub><sub>1</sub><sub>||</sub><sub>K</sub><sub>client</sub><sub>)</sub> and compares the result to M2. If they do not match, the authentication has failed.</li>

 <li>The Server closes the socket and waits for further connections.</li>

</ol>

Steps 1-3 generate the authenticated key shared between the Client and the Server. Steps 4-7 verify that both parties have computed the same shared key. If executed honestly, <sub>K</sub><sub>client</sub><sup> and</sup><sub> K</sub><sub>server</sub> are equal and the Server and Client were able to authenticate each other and establish a shared session key.

<ul>

 <li>At the end of either registration or the protocol, the Server should resume listening on the socket.</li>

</ul>

<sup>5</sup>The program template will do this for you, as well as check that the length of the username encodes to less than 255 bytes.

<sup>6</sup>In cryptography, a salt is a random piece of data used as an additional input to a one-way function that hashes data, a password or passphrase.




<ul>

 <li>Note that in order to reliably receive information from the socket, the byte length of the data must typically be known. Unless otherwise specified, the size of any value taken modulo N should be the same length as N (up to 512 bits). Since SHA2-256 is used, any hashed value that is not taken modulo N is therefore 256 bits in size. The encoded username may be up to 255 bytes in length.</li>

 <li>Please note the importance of the order that values are sent over the socket. Problem. Your task is to complete the template program named</li>

</ul>

basic <a href="http://auth.py">auth.py</a>

which performs the above password-based key agreement protocol. The program consists of func­tions corresponding to establishing a connection and transmitting data through a socket, parameter generation, and the actions performed by the Client and the Server.

All messages over the socket should be echoed to standard output by both the sending and receiving party. Each echoed message should clearly indicate its sender and intended receiver. Use a template like the following:<sup>7</sup>

Server: N = (integer value of N)

Client: Received &lt;(hex representation of incoming data)&gt; Server: Authentication was successful.

Client: ERROR, the socket was closed.

For this exercise the hash function H will be SHA2-256 as implemented in the cryptography library. Additionally, when randomness is required use either os.urandom or the secrets library. We will allow use of the sympy library, as it is useful for handling prime numbers; however, you are expected to implement the function prim root on your own, and you may not use sympy’s primitive root() method in your implementation.

Specifications. Fill in the empty functions in the template program basic <a href="http://auth.py">auth.py</a>. Once com­plete, you should be able to perform both registration and key agreement between two parties, one acting as the Client and the other as Server, by running

python3 basic <a href="http://auth.py">auth.py</a> –server 127.0.4.18:3180 python3 basic <a href="http://auth.py">auth.py</a> –client 127.0.4.18:3180 python3 basic <a href="http://auth.py">auth.py</a> –quit 127.0.4.18:3180

You may also combine these actions with one invocation of basic <a href="http://auth.py">auth.py</a>, although this makes debugging substantially more difficult. There will be additional command-line options to change the username and password from the defaults.

In detail, the functions you’ll need to fill in fall into roughly three categories:

<ol>

 <li>Networking Functions:</li>

</ol>

(i) create socket(…), which creates a socket connection on the specified IP and port.

<sup>7</sup>The printed text is primarily for human eyes, not computer parsing, so there is no need to match these examples precisely.




<ul>

 <li>send(…), which sends bytes through the specified socket.</li>

 <li>receive(…), which receives a specified bytes through the socket.</li>

</ul>

<ol>

 <li>Low-level Functions:</li>

</ol>

<ul>

 <li>safe prime(…), which creates a random safe prime N of a specified bit-length and whose most significant bit is 1.</li>

 <li>prim root(…), which finds a primitive root g of N for some prime N.</li>

</ul>

Note: You may not use sympy’s primitive root method for your implemen­tation.

<ul>

 <li>calc x(…), which computes the value x from the registration step using the salt and</li>

 <li>calc u(…), which computes the value u using the provided inputs.</li>

 <li>calc A(…), which computes the value A using the provided inputs.</li>

 <li>calc B(…), which computes the value B using the provided inputs.</li>

 <li>calc K client(…), which computes the value Kclient.</li>

 <li>calc K server(…), which computes the value Kserver.</li>

 <li>calc M1(…), which computes the value M1.</li>

 <li>calc M2(…), which computes the value M2.</li>

</ul>

<ol>

 <li>High-level Functions:</li>

</ol>

<ul>

 <li>client register(…), which sends and receives information to and from the Server as described in the Client registration.</li>

 <li>server register(…), which receives and sends information from and to the Client through the socket connection, as outlined in the Server registration.</li>

 <li>client protocol(…), which performs the Client’s side of the protocol.</li>

 <li>server protocol(…), which performs the Server’s side of the protocol.</li>

 <li>client prepare(…), which computes the Client’s registration tuple (username, s, v).</li>

 <li>server prepare(…), which computes the Server’s registration values N,g, k.</li>

</ul>

Note that some values may be supplied as an integer or as a bytes object; your functions will need to translate between them as the context requires. All numbers are converted to bytes via network byte order, which is big-endian.<sup>8</sup> Additional details and documentation of these functions can be found in the template program found on the Piazza resources page.

Submission. Submit a completed version of the template program with filename

basic <a href="http://auth.py">auth.py</a>

If you’ve spread your code across multiple source files, submit all of them.

Provide a description of your implementation in a separate README file in text format. Do not include the written portion of the programming problem in the PDF file containing your solutions to the written problems. Your description should include the following:

<ul>

 <li>The procedures you used for generating your prime N and your primitive root g of N.</li>

 <li>A list of the files you have submitted that pertain to the problem, and a short description of each file.</li>

 <li>A list of what is implemented in the event that you are submitting a partial solution, or a statement that the problem is solved in full.</li>

 <li>A list of what is not implemented in the event that you are submitting a partial solution.</li>

 <li>A list of known bugs, or a statement that there are no known bugs.</li>

</ul>

<sup>8</sup>Functions will be supplied with the template to help with conversion.