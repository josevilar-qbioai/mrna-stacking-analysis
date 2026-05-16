# Nearest-Neighbor Stacking ΔG Profiles for mRNA Codon Optimization

Reproducible analysis code and data for the paper:

> **Nearest-Neighbor Stacking Free Energy Profiles as a Complementary Dimension for mRNA Codon Optimization**
>
> Jose Antonio Vilar Sanchez (2026)
>
> DOI: [10.5281/zenodo.20228980](https://doi.org/10.5281/zenodo.20228980)

## Overview

This repository demonstrates that nearest-neighbor stacking free energy (ΔG) profiles constitute a complementary optimization dimension for therapeutic mRNA design, independent of secondary structure MFE and superior to GC3 at local resolution.

### Key findings

- **Vaccine ΔG shift:** BNT162b2 and mRNA-1273 show ΔΔG = −0.30 to −0.36 kcal/mol vs. native spike
- **Complementarity:** Stacking ΔG vs. secondary structure MFE → R² = 0.144 (independent dimensions)
- **Expression link:** ΔG vs. CSC at codon level: r = −0.501
- **Universality:** 9/9 human genes maintain ΔG(AT) > ΔG(native) > ΔG(GC), mean effect −0.416 kcal/mol
- **Local resolution:** Intra-gene residual beyond GC3: r = −0.378 (p = 6.8×10⁻³⁰), ΔR² = +5.0%

## Repository structure

```
mrna-stacking-analysis/
├── core/
│   └── energy.py              # Nearest-neighbor ΔG engine (SantaLucia 1998)
├── notebooks/
│   ├── 01_vaccine_profiles.ipynb       # Fig 1: BNT162b2 vs mRNA-1273 vs native
│   ├── 02_structure_vs_stacking.ipynb  # Fig 2: MFE complementarity (R² = 0.144)
│   ├── 03_expression_correlation.ipynb # Fig 3: ΔG–CSC codon-level link
│   └── 04_multigene_and_residual.ipynb # Fig 4–5: 9-gene validation + residual
├── data/
│   ├── *.fasta                # Vaccine and native spike sequences
│   └── *.csv                  # Pre-computed analysis results
├── figures/                   # Publication-quality figures (PNG)
├── references.bib             # Bibliography
├── environment.yml            # Conda environment
├── LICENSE                    # MIT
└── CITATION.cff               # Citation metadata
```

## Quick start

```bash
# Clone and set up environment
git clone https://github.com/josevilar-qbioai/mrna-stacking-analysis.git
cd mrna-stacking-analysis
conda env create -f environment.yml
conda activate mrna-stacking

# Run notebooks
jupyter notebook notebooks/
```

## Shared engine

The thermodynamic engine (`core/energy.py`) implements SantaLucia (1998) unified nearest-neighbor parameters. The same code powers [EnergyFingerprint](https://github.com/josevilar-qbioai/energyfingerprint) for missense variant classification (patent P202630522, OEPM 2026).

## Requirements

- Python ≥ 3.10
- NumPy, Pandas, SciPy, Matplotlib
- ViennaRNA 2.7+ (for notebook 02, secondary structure analysis)

See `environment.yml` for the complete specification.

## Citation

If you use this code or data, please cite:

```bibtex
@misc{vilar2026mrna,
  author = {Vilar Sanchez, Jose Antonio},
  title = {Nearest-Neighbor Stacking Free Energy Profiles as a Complementary
           Dimension for mRNA Codon Optimization},
  year = {2026},
  publisher = {GitHub},
  url = {https://github.com/josevilar-qbioai/mrna-stacking-analysis}
}
```

## Related work

- [EnergyFingerprint](https://github.com/josevilar-qbioai/energyfingerprint) — Variant classification using thermodynamic mRNA profiles
- SantaLucia (1998) — [doi:10.1073/pnas.95.4.1460](https://doi.org/10.1073/pnas.95.4.1460)
- LinearDesign (Zhang et al. 2023) — [doi:10.1038/s41586-023-06127-z](https://doi.org/10.1038/s41586-023-06127-z)

## Patent notice

The nearest-neighbor stacking thermodynamic profiling method used in this work is protected under Spanish Patent Application **P202630522** ("Método de huella termodinámica del mRNA", OEPM 2026). The code in this repository is released under the MIT License for academic and research purposes. Commercial use of the patented method may require a license from the patent holder.

## License

MIT License. See [LICENSE](LICENSE).

## Author

**Jose Antonio Vilar Sanchez**
- ORCID: [0009-0008-1057-4223](https://orcid.org/0009-0008-1057-4223)
- GitHub: [@josevilar-qbioai](https://github.com/josevilar-qbioai)
- Contact: qmetrika@proton.me
