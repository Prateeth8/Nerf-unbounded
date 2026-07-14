# Nerf-unbounded

This repository contains notebook implementations for training and evaluating NeRF-style models on outdoor Mip-NeRF 360 data.

## Repository structure

- `code/nerf_ver1.ipynb` - initial NeRF training notebook with dataset loading and model definitions.
- `code/test_ver1.ipynb` - initial testing notebook for evaluating the trained NeRF model.
- `code/nerf_ver2.ipynb` - combined training and test notebook with improved dataset handling, pose normalization, LLFF-to-OpenGL conversion, and full end-to-end train/test flow.
- `mod_weights/best_nerf_weights.pth` - sample model weights saved from training.
- `requirements.txt` - Python package requirements for running the notebooks.

## Dependencies

Install the dependencies with:

```bash
pip install -r requirements.txt
```

The repository depends on:

- `torch` for model definition, training, and inference
- `numpy` for numeric and data handling
- `Pillow` for image loading and saving
- `tqdm` for progress display
- `opencv-python` for optional image or video utilities used in the notebook versions
- `jupyter` for running notebooks

## Notebook overview

### `code/nerf_ver1.ipynb`
- Defines a Kaggle-style MipNeRF dataset loader.
- Builds a NeRF MLP model with positional encoding and Mip-NeRF contraction.
- Contains training and evaluation functions.
- Uses `cv2`, `torch`, `numpy`, `PIL`, and `tqdm`.

### `code/test_ver1.ipynb`
- Contains evaluation/inference logic for a trained NeRF model.
- Uses the same model and ray rendering functions as `nerf_ver1`.
- Designed to test saved model weights and render output images.

### `code/nerf_ver2.ipynb`
- A more complete combined train/test notebook.
- Includes improved dataset pose handling and multi-resolution input support.
- Implements LLFF-to-OpenGL pose conversion and sphere normalization.
- Trains a NeRF model and then evaluates on a test set with chunked rendering.

## Running the notebooks

Open the repository in Jupyter or VS Code and run the notebooks in sequence.

1. Start with `code/nerf_ver1.ipynb` if you want to inspect the initial model/data workflow.
2. Use `code/test_ver1.ipynb` for standalone model evaluation.
3. Use `code/nerf_ver2.ipynb` for a full training and testing pipeline.

## Notes

- The notebooks assume access to a Mip-NeRF 360 dataset with `poses_bounds.npy` and image directories.
- `nerf_ver2.ipynb` uses relative or Kaggle-style dataset paths; update `base_dir` to your data location if necessary.
- Training NeRF models can be expensive; reduce image resolution and ray batch sizes when running on limited hardware.
