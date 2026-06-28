### 00_setup
Das erste Skript  00_setup.R lädt lediglich einige Libraries, definierte einige Variablen und lädt ggf. den Speicherstand. Sollte auf jeden Fall immer durchlaufen

### 01_functions
Im zweiten Skript werden all die verwendeten Funktionen definiert. Sie sind eingeteilt in 
  - Data Generating Process
  - Estimation
  - True Parameter
  - Joint Distribution
  - Long run Covariance
  - Asymptotic Distribution
  - Simulation
  - Plot
Da hier sowieso noch nichts simuliert wird, am besten alles durchlaufen lassen.

### 02_run_sim
Hier werden noch eine Preprocessing Schritte gemacht und die verschiedenen Simulationen. Die verschiedenen Szenarien oben können wohl am besten alle mal geladen werden. 

Danach lohnt es sich nur die relevanten Simulationen zu laden.

- Die Hauptsimulation ist relevant für die ganzen Comparison Plots
- MAR-Simulationen sind relevant für die letzten beiden Plots, wobei
  - `results_MAR` und `results_MAR_inv` für den Plot für IOV unter MNAR relevant sind
  - `kappa_inc_list` und `kappa_dec_list` für die linke Seite des letzten Plots
  - `rej_list_mnar` / `rej_df_mnar` für die rechte Seite des letzten Plots
- Bias/CLT Simulation:
  - `sim_data` (also auch `sim_50` usw.) für den CLT Plot
  - `sim_data_2` für die Biasplots
- Kappa $H_0$ Simulationen (`rej_h0_list` / `rej_H0_df`) für den Plot Rejection Rates unter $H_0$
- Kappa $H_A$ Simulationen für die beiden Plots bezüglich $\kappa(h)$ unter $H_A$:
  - `kappa_HA_df` / `kappa_summary` / `ci_df` für den linken Plot (Konfidenzintervalle)
  - `rej_list` / `rej_df` für den rechten Plot (Rejectionrates)

### 03_run_asymp
Erstellt asymptotisch berechnete Objekte ensprechend dem paper
  - `asymp_df` für all die "Comparison-Plots"
  - `Sigma_raw` für die Bias Plots

### 04_visuals
Hier ist der Code für die Plots mit einigen weiteren preprocessing Schritten. Die plots sind weitestegehend entsprechend der Ordnung im Paper angeordnet. Bloß die Comparison-Plots (Figures 4.6- 4.9) ist erst nach Szenarios, dann nach Reihenfolge der Plots im Paper sortiert, wobei das Szenario mit serieller Abhängigkeit von $O_t$ im selben Block unten separat behandelt wird.
