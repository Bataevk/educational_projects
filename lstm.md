```mermaid
flowchart TD
  X_t[X_t]
  H_t_minus1[H_{t-1}]
  Concat1[concat X_t and H_{t-1}]

  LF[W_f · concat + b_f]
  LI[W_i · concat + b_i]
  LC[W_c · concat + b_c]
  LO[W_o · concat + b_o]

  SF[sigma f_t]
  SI[sigma i_t]
  TC[tanh c̃_t]
  SO[sigma o_t]

  M1[f_t * c_{t-1}]
  M2[i_t * c̃_t]
  SumC[c_t]
  TC2[tanh c_t]
  Out[h_t]

  X_t --> Concat1
  H_t_minus1 --> Concat1

  Concat1 --> LF --> SF
  Concat1 --> LI --> SI
  Concat1 --> LC --> TC
  Concat1 --> LO --> SO

  SF --> M1
  H_t_minus1 --> M1
  M1 --> SumC

  SI --> M2
  TC --> M2
  M2 --> SumC

  SumC --> TC2
  TC2 --> Out
  SO --> Out
```
