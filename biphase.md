# Biphase

### ![image](https://user-images.githubusercontent.com/62918160/128657208-3d6125f2-0c87-441f-bdfc-5ed7145cdcb1.png)

### Types of Encoding -->
Biphase-manchester: Transition from high to low in middle of interval = 1 and Transition from low to high in middle of interval = 0

Differential-manchester: Always a transition in middle of interval. No transition at beginning of interval=1 and Transition at beginning of interval = 0

4B/5B Encoding: In Manchester encoding scheme , there is a transition after every bit. It means that we must have clocks with double the speed to send same amount of data as in NRZ encodings. In other words, we may say that only 50% of the data is sent. This performance factor can be significantly improved if we use a better encoding scheme. This scheme may have a transition after fixed number of bits instead of every other bit. Like if we have a transition after every four bits, then we will be sending 80% data of actual capacity. This is a significant improvement in the performance.

This scheme is known as 4B/5B. So here we convert 4-bits to 5-bits, ensuring at least one transition in them. The basic idea here is that 5-bit code selected must have :
one leading 0
no more than two trailing 0s
Thus it is ensured that we can never have more than three consecutive 0s. Now these 5-bit codes are transmitted using NRZI coding thus problem of consecutive 1s is solved.
 



