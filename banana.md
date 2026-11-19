Exp 2:basic communication system

import numpy as np
import matplotlib.pyplot as plt

# Generate 10 random bits
bits = np.random.randint(0, 2, 10)
print("Original bits:", bits)

# Convert bits to BPSK symbols (0 -> -1, 1 -> +1)
signal = 2 * bits - 1
print("Transmitted signal:", signal)

# Generate Gaussian noise and add it to the signal
noise = np.random.normal(0, 0.5, 10)
received_signal = signal + noise
print("Received signal:", received_signal)

# Plot both signals on the same graph
plt.figure(figsize=(8, 4))
plt.plot(signal, 'bo-', label='Transmitted Signal')
plt.plot(received_signal, 'r*-', label='Received Signal')
plt.title("Basic Communication System")
plt.xlabel("Bit Number")
plt.ylabel("Signal Amplitude")
plt.grid(True)
plt.legend()
plt.show()

explanation:

### BPSK practical in 4 steps

1. **Generate bits.** `np.random.randint(0, 2, 10)` creates 10 random bits, each `0` or `1`.
2. **Modulate.** `signal = 2 * bits - 1` maps `0` to `−1` and `1` to `+1`. These represent the 
two carrier phases of BPSK, separated by **180°**.
3. **Add noise.** Generate one Gaussian noise value per symbol and add it using 
`received_signal = signal + noise`.
4. **Plot and compare.** Blue circles show the transmitted symbols. Red stars show
the received values. The gap between the markers at the same bit position shows how much noise changed the signal.

**Say this in your viva**

> “I generate ten random bits and convert them to BPSK symbols, minus one and plus one. Then I add Gaussian noise to 
simulate transmission. Finally, I plot both signals on the same graph to show the effect of noise. If the received value 
stays on the same side of zero as the transmitted symbol, it would decode to the same bit.”

#Exp3 frequency reuse

import matplotlib.pyplot as plt
import numpy as np

pts=[[0,0],[2,0],[-2,0],[1,1.73],[-1,1.73],[1,-1.73],[-1,-1.73]]
col=['red','blue','orange','pink','purple','green','cyan']

r=1
n=7
d=((3*n)**0.5)*r
a=np.linspace(0,2*np.pi,7)

for i in range(7):
	x,y=pts[i]

	plt.fill(x+np.cos(a),y+np.sin(a),col[i])
	plt.text(x,y,'F'+str(i))

	plt.fill((x+d)+np.cos(a),y+np.sin(a),col[i])
	plt.text(x+d,y,'F'+str(i))

plt.plot([0,d],[0,0],'k--')
plt.show()

steps
1. Draw the first cluster of seven hexagonal cells and label them F1 to F7.
2. Locate the next F1 cell. From the first F1 center, move 2 cells straight, turn 60°, and move 1 more cell.
3. Repeat F1 to F7 in the second cluster. The two F1 cells use the same frequency group, so they are co-channel cells.
4. Draw a dashed line between the two F1 centers. Its length is the reuse distance, \(D=R\sqrt{3N}=4.58\) units for \(R=1\).
Formula to remember: \(N=i^2+ij+j^2=2^2+2(1)+1^2=7\)

exp10/pathloss
https://wc-iiith.vlabs.ac.in/exp/pathloss-shadowing/simulation.html























