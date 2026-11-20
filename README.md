# Training a Robust Model from the Orbits of Neural Networks

Working paper by William Chuang (2023), with its LaTeX source and figures.

## Question

Given a trained neural network, can infinitely many *equivalent* models be generated from it: models that give the same outputs on the training data, give different outputs out of sample, and still receive non-trivial gradients when trained further?

## Method

- Each weight is mapped to a point of the upper half-plane ℍ².
- The matrix product is replaced by the **hyperbolic-length product**

  $$(A \odot_{\mathbb{H}^2} B^t)_{kl} = \sum_{i=1}^{m} d_{\mathbb{H}^2}(a_{ki}, b_{il}).$$

- Every element of PSL(2, ℝ) acts on ℍ² as a Möbius isometry, so applying one map $T_M$ to all weights leaves the product unchanged. The images of the weights under all such maps form the **orbit** of the model.
- Möbius maps are fractional linear rather than linear, so a model moved along its orbit receives non-trivial gradients in back-propagation; the Discussion section derives these gradients explicitly.
- The paper relates the orbit of a model to its position on the loss surface, through two-generator (Schottky) subgroups of PSL(2, ℝ) and the Teichmüller space of the associated hyperbolic surface.

## Contents

| Path | Content |
|---|---|
| `orbits_of_neural_networks.tex` | Paper source |
| `orbits_of_neural_networks.pdf` | Compiled paper |
| `refs.bib` | Bibliography |
| `figures/` | Figures used in the paper |
| `computational_graph.pdf` | Computational graph of the hyperbolic-orbit algorithm |

## Building the paper

```bash
pdflatex orbits_of_neural_networks
bibtex   orbits_of_neural_networks
pdflatex orbits_of_neural_networks
pdflatex orbits_of_neural_networks
```

Requires a TeX Live installation with `tikz`, `tcolorbox`, `algorithm2e` and `listings`.

## Status

Working paper. Section 5 (Empirical Results) has not been written yet.

## Citation

```bibtex
@misc{chuang2023orbits,
  author = {Chuang, William},
  title  = {Training a Robust Model from the Orbits of Neural Networks},
  year   = {2023},
  note   = {Working paper},
  url    = {https://github.com/williamchuang/orbits-of-neural-networks}
}
```

## License

MIT — see [LICENSE](LICENSE).
