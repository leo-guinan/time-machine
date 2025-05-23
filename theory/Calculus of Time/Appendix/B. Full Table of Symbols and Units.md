# Appendix B – Table of Symbols and Units

## Core Concepts

|Symbol|Definition|Units|Example Value|
|---|---|---|---|
|C(S)|Complete change set of system S|[dimensionless set]|{accident occurs, ambulance arrives, traffic builds}|
|O(S)|Observation set sampled from C(S)|[dimensionless set]|{accident occurs, ambulance arrives}|
|V(S)|Verification set validated from O(S)|[dimensionless set]|{accident occurs [verified]}|

## Sampling and Processing Functions

|Symbol|Definition|Units|Example Value|
|---|---|---|---|
|ψ_i|Observation function for node i|[info units/time]|ψ_Sarah = 4 units/min|
|φ_i|Verification function for node i|[info units/time]|φ_David = 2 units/min|
|v_o|Observation velocity|[info units/time]|4 units/min|
|v_v|Verification velocity|[info units/time]|2 units/min|
|v_v^(T)|Trust-modified verification velocity|[info units/time]|3 units/min (when T=0.8)|

## Time and Distance Variables

|Symbol|Definition|Units|Example Value|
|---|---|---|---|
|t_c|Time of change occurrence|[time]|6:47 AM|
|t_o(d)|Observation time at distance d|[time]|6:49 AM (d=1)|
|t_v(d)|Verification completion time at distance d|[time]|6:51 AM (d=1)|
|τ_i|Temporal coordinate for change i|[time]|6:47:15 AM|
|Δt_i|Duration of change i|[time]|3 minutes|
|d_ij|Network distance between nodes i,j|[hops]|2 hops|

## Network Properties

|Symbol|Definition|Units|Example Value|
|---|---|---|---|
|C_N|Network invariant speed|[info units/time]|1.33 units/min|
|C_N(d)|Distance-degraded invariant speed|[info units/time]|1.1 units/min (d=2)|
|T_ij|Trust coefficient from node i to j|[dimensionless] ∈ [0,1]|0.8|
|R(d)|Resolution preservation at distance d|[dimensionless] ∈ [0,1]|0.85|

## Dilation and Contraction Factors

|Symbol|Definition|Units|Example Value|
|---|---|---|---|
|γ_i|Time dilation factor for node i|[dimensionless]|1.4|
|τ_eff(i)|Effective time rate for node i|[events/time]|5.6 events/min|
|η_temporal(i)|Temporal efficiency for node i|[dimensionless] ∈ [0,1]|0.73|
|V_overhead(i)|Verification overhead for node i|[dimensionless] ∈ [0,1]|0.27|

## Information Quality Measures

|Symbol|Definition|Units|Example Value|
|---|---|---|---|
|Δ_i|Significance/magnitude of change i|[dimensionless]|0.8|
|H(X)|Information entropy of set X|[bits]|3.2 bits|
|I(X;Y)|Mutual information between X and Y|[bits]|1.7 bits|
|F(U_S, U)|Fidelity between sub-network and parent|[dimensionless] ∈ [0,1]|0.92|

## Sub-Network Universe Parameters

|Symbol|Definition|Units|Example Value|
|---|---|---|---|
|U_S|Sub-network universe|[structured set]|Management level|
|N_S|Node set in sub-network|[dimensionless set]|{Sarah, David, Lisa}|
|E_S|Edge set in sub-network|[dimensionless set]|{Sarah→David, David→Lisa}|
|B_S|Boundary interface set|[dimensionless set]|{David↔Executive}|
|Φ_S|Mapping function to parent network|[function]|Detail→Summary|
|C(U_S)|Compression ratio of sub-network|[dimensionless]|10:1|

## Scaling and Weighting Parameters

|Symbol|Definition|Units|Example Value|
|---|---|---|---|
|α|Trust scaling parameter|[dimensionless]|0.6|
|β|Learning rate parameter|[1/time]|0.1 min^-1|
|λ|Information arrival rate|[info units/time]|1.3 units/min|
|w_i|Importance weight for node i|[dimensionless]|0.7|

## Common Derived Quantities

|Symbol|Definition|Formula|Units|
|---|---|---|---|
|Processing Rate|Effective throughput|min(v_o, v_v, λ)|[info units/time]|
|Trust Acceleration|Speedup from trust|1 + α·T_ij|[dimensionless]|
|Verification Efficiency|Productive vs. overhead|1 - V_overhead|[dimensionless]|
|Network Diameter|Maximum distance|max{d_ij}|[hops]|
|Temporal Gradient|Time rate variation|dτ_eff/dd|[1/distance]|

## Unit Conventions

**Information Unit**: A discrete, independently verifiable claim or observation

- Examples: "Temperature is 72°F", "Meeting starts at 3 PM", "Document approved"
- Properties: Atomic (cannot be subdivided), Verifiable (can be validated), Transmissible (can be communicated)

**Time Unit**: Typically minutes for human networks, seconds for digital networks, hours for organizational networks

**Distance Unit**: Network hops (minimum number of node-to-node transmissions required)

**Dimensionless Quantities**: Ratios, probabilities, and efficiency measures ranging from 0 to 1 unless otherwise specified

---

_This table provides reference definitions for all mathematical symbols used in the Network Relativity framework. For narrative context, see the Morning Misinformation Network example in Section 2.0._
