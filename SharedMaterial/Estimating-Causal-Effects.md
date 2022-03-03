## Example research question:

Giả sử ta cần ước tính tác động nhân quả của của việc có bằng đại học và thành công ở tuổi 40

Y (outcome)= Thành công ở tuổi 40 <br />
D (treatment) = Có bằng đại học hay không Y/N <br />
S = các biến được lựa chọn quan sát <br />
i (Individual) =  một cá nhân (một mẫu)  <br />

<img src="https://latex.codecogs.com/png.image?\dpi{300}&space;\bg_white&space;\delta_i&space;=&space;Y^1_{i}&space;-&space;Y^0_{i}&space;" title="\bg_white \delta_i = Y^1_{i} - Y^0_{i} " />

$Y^1_i$ - kết quả có thể xảy ra trong treament state cho mẫu i <br>
$Y^0_i$ Kết quả có thể xảy ra trong control state cho mẫu i

$Y_i = Y^1_i \space if \space D_i = 1$ <br>
$Y_i = Y^0_i\space if \space D_i = 0$ 

Biến tác động (treatment) được biểu diễn là D với D = 1 biểu thị treatment và D = 0 biểu thị control

Công thức thường được viết dưới dạng:
$Y_i = D_iY^1_i + (1 - D_i)Y^0_i$ 

**Aggregated Causal Effects:**
$E[\delta_i] = E[Y^1_i] - E[Y^0_i]$


**Avg Treatment Effect of the Treated:** $E[\delta_i | D_i = 1] = E[Y^1_i | D_i = 1] - E[Y^0_i|D_i = 1]$


**Avg Treatment Effect of the Untreated:** $E[\delta_i | D_i = 0] = E[Y^1_i | D_i = 0] - E[Y^0_i|D_i = 0]$

**Naive Estimator:** $\delta_{NAIVE} \equiv E_N[y_i|d_i = 1] - E_N[y_i | d=0]$

$E_N[y_i|d_i=1]$ - trung bình mẫu của outcome với những treatment

$E_N[y_i|d_i=0]$ - trung bình mẫu của outcome với những control

Giả sử S ở ví dụ trên là các yếu tố về hoàn cảnh gia đình và sự chuẩn bị cho đại học

$\Rightarrow E_N = [y_i | d_i = 1] = E[Y| D=1]$

Ví dụ ta cho bảng phân phối xác xuất kết của 2 biến S và D
|     	| D=0  	| D= 1 	|      	|
|:---:	|------	|------	|------	|
| S=1 	| 0.36 	| 0.08 	| 0.44 	|
| S=2 	| 0.12 	| 0.12 	| 0.24 	|
| S=3 	| 0.12 	| 0.2  	| 0.32 	|
|     	| 0.6  	| 0.4  	|      	|

|     	|  Trung bình với Control 	| Trung bình với Treatment  	|      	|
|:---:	|------	|------	|------	|
| S=1 	| 2 	| 4 	|$E[\delta \| S=1] = 2$|
| S=2 	| 6 	| 8 	|$E[\delta \| S=2] = 2$|
| S=3 	| 10 	| 14  	|$E[\delta \| S=3] = 4$|
|     	| 4.4  	| 10.2  	|      	|

$E[Y^0|D=0] = \frac{0.36}{0.6}(2) + \frac{0.12}{0.6}(6) + \frac{0.12}{0.6}(10) = 4.4$

$E[Y^0|D=1] = \frac{0.08}{0.4}(4) + \frac{0.12}{0.4}(8) + \frac{0.2}{0.4}(14) = 10.2$

**Ước lượng xác xuất của S với điều kiện D**
|     	|   	|  	    |
|:---:	|------	|------	|
| S=1 	| $P_N[S_i = 1 \| D_i = 0] = 0.6$	|$P_N[S_i = 1 \| D_i = 1] = 0.2$|
| S=2 	| $P_N[S_i = 2 \| D_i = 0] = 0.2$	|$P_N[S_i = 2 \| D_i = 1] = 0.3$|
| S=3 	| $P_N[S_i = 3 \| D_i = 0] = 0.2$	|$P_N[S_i = 3 \| D_i = 1] = 0.5$|

$ATT =\sum_{i=1}^3{E[\delta\|S=i] \times P_N[S = i \| D = 1]}  = 3$ <br><br>
$ATC =\sum_{i=1}^3{E[\delta\|S=i] \times P_N[S = i \| D = 0]}  = 2.4$ <br><br>
$ATE = ATT \times P[D=1] + ATC \times P[D=0] = 3(0.4) + 2.4(0.6) = 2.64$