# Customer Intelligence and Inventory Optimization Using Predictive and Agentic AI

This repository contains the publicly released implementation of the core experimental components of the Seven-Layer Retail Intelligence Architecture proposed in this research.

The framework investigates the integration of customer-review sentiment analysis, demand forecasting, reinforcement-learning-based inventory control, and agentic AI within a retail decision-support architecture. The repository provides the sentiment-classification, synthetic-demand forecasting, and DQN-based inventory-control experiments used in the manuscript.

The architecture is presented as a conceptual multi-layer framework. The current public implementation does not constitute a fully connected end-to-end execution pipeline from DistilBERT sentiment outputs through forecasting into the DQN inventory state.

---

## Repository Structure

- **`DistilBert_Experiment_Final.ipynb`**  
  Final large-scale DistilBERT sentiment classification experiment (Experiment 9, n = 883,636).

- **`Distillbert_Experiment_1.ipynb` – `Distillbert_Experiment_8.ipynb`**  
  Preliminary DistilBERT experiments used for hyperparameter and dataset-scale evaluation.

- **`DQN_AGENT.ipynb`**  
  PyTorch implementation of the Deep Q-Network (DQN) agent for simulated inventory replenishment.

- **`sales_db_random.ipynb`**  
  Notebook for synthetic demand-data generation and baseline forecasting experiments.

---

## Dataset

The synthetic demand dataset and curated processed data used in this research are openly deposited on Zenodo:

**Zenodo DOI:**  
https://doi.org/10.5281/zenodo.20573668

The Amazon Fashion review data used for sentiment-model training are sourced from the publicly available Amazon Review Data (2018) project:

**Amazon Review Data (2018):**  
https://nijianmo.github.io/amazon/index

To reproduce the experiments, download the required datasets and place them in the working project directory as expected by the notebooks.

---

## Experimental Components

### 1. DistilBERT Sentiment Classification

`DistilBert_Experiment_Final.ipynb` contains the final large-scale sentiment-classification experiment.

Experiment 9 uses 883,636 review records and represents the final large-scale configuration evaluated in the manuscript.

The repository also contains the preliminary Experiments 1–8, which were used to evaluate different training configurations and dataset scales.

### 2. Demand Forecasting

`sales_db_random.ipynb` contains the synthetic demand-data generation and baseline forecasting experiments.

The forecasting evaluation includes:

- Naive last-observed-month baseline
- 12-month moving average
- 48-month historical mean
- Sentiment-enhanced forecasting

The synthetic demand dataset does not encode an empirical sentiment-demand relationship. Therefore, the forecasting results are interpreted as a methodological proof of concept rather than evidence of a real-world causal relationship between customer sentiment and demand.

### 3. DQN Inventory Control

`DQN_AGENT.ipynb` contains the PyTorch implementation of the Deep Q-Network (DQN) inventory-control simulator.

The current implementation uses a simulated inventory environment trained for 1,400 episodes.

#### Reward Configuration

The current DQN implementation uses:

- Holding-cost coefficient (Ch): 0.10
- Stockout-penalty coefficient (Cs): 2.50

The stockout penalty is scaled using the synthetic customer-weight variable.

The current implementation uses synthetically initialized auxiliary state variables:

- Sentiment: sampled from the simulated sentiment states
- Customer weight: synthetically initialized for the inventory-control environment

These variables are not directly derived from the DistilBERT sentiment outputs in the current implementation.

Therefore, the DQN experiment should be interpreted as a reproducible inventory-control proof of concept rather than as an empirically validated sentiment-driven inventory optimization system.

---

## Getting Started

### 1. Clone the Repository

    git clone https://github.com/imujjwalkant/Customer-Intelligence-Inventory-Optimization-AI.git
    cd Customer-Intelligence-Inventory-Optimization-AI

### 2. Install Dependencies

Ensure that Python 3.8+ and Jupyter are installed, then install the required libraries:

    pip install torch transformers pandas numpy scikit-learn matplotlib seaborn jupyter

### 3. Run the Experiments

#### Sentiment Classification

Open:

    DistilBert_Experiment_Final.ipynb

to reproduce the final large-scale DistilBERT sentiment-classification experiment.

#### Demand Forecasting

Open:

    sales_db_random.ipynb

to generate or evaluate the synthetic demand data and forecasting baselines.

#### Inventory Optimization

Open:

    DQN_AGENT.ipynb

to execute the DQN inventory-control simulator.

---

## Reproducibility Scope

The repository provides the source notebooks corresponding to the core quantitative experiments reported in the manuscript.

The publicly released components include:

- DistilBERT sentiment-classification experiments
- Synthetic demand-data generation
- Forecasting baseline experiments
- DQN-based inventory-control simulation

The Streamlit dashboard and Llama 3 8B product-intelligence prototype are not included in the current public repository.

These components are therefore treated as prototype/interface layers and are not claimed as independently reproducible experimental components in the current manuscript.

The quantitative results reported in the paper are restricted to experiments for which the corresponding data, implementation, and evaluation procedures are documented or publicly deposited.

---

## Research Scope and Limitations

The current repository represents a multi-component research proof of concept.

In particular:

1. The synthetic demand data do not represent real transactional retail data.
2. The synthetic demand data do not encode an empirical sentiment-demand relationship.
3. The current DQN implementation does not directly consume DistilBERT sentiment outputs.
4. The DQN environment does not model all real-world supply-chain constraints, such as supplier lead times, minimum order quantities, logistics constraints, and demand shocks.
5. The Streamlit dashboard and Llama 3 8B prototype are not currently included in the public repository.

Future work will focus on validating the framework using matched real-world review and transactional data and establishing a controlled connection between customer sentiment, demand forecasting, and inventory-control state variables.

---

## Citation

Author: Ujjwal Kant  
ORCID: 0009-0003-6372-3214  
Target Journal: IEEE Access

If you use this repository or the associated research, please cite:

    @unpublished{kant2026customer,
      title={Customer Intelligence and Inventory Optimization Using Predictive and Agentic AI},
      author={Kant, Ujjwal},
      note={Manuscript submitted to IEEE Access},
      year={2026}
    }

---

## Related Research

Ujjwal Kant, "Customer Intelligence and Inventory Optimization Using Predictive and Agentic AI," M.S. thesis, Liverpool John Moores University, Liverpool, U.K., 2026.

---

## License

This repository is provided for research and academic purposes. Please refer to the repository license and individual dataset terms before redistributing or using the materials for other purposes.
