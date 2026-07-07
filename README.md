# Assignment 4  Watermark Forgery Attack
The folder contains the code and the steps to achieve the best score in assignment 4  Watermark Forgery Attack.

## Files
- README.md - explains how to recreate the best result
- freq_band_mix.py - contains the script for best score
- submission.py - submission script to submit the final zip to leaderboard
- freq_wm3_spatial_mid_a055.zip - final submitted zip file
- combo_wm7blue_wm6_sota - precomputed base fored candidate
- forged_spatial_a2.5_b41 - precomputed alternative forged candidate

How to Setup and Run :

1. Create the working directory,
    `mkdir -p ~/tml26_task4`
    `cd ~/tml26_task4`
2. Create and then activate the python virtual environment,
    ```
    python3 -m venv .venv
    source .venv/bin/activate
    ```
3. The install the python dependencies,
    ```
    pip install --upgrade pip
    pip install numpy pillow tqdm matplotlib requests huggingface_hub
    ```
4. Install Git LFS if not installed
5. Then clone the Hugging Face dataset given,
    ```
    cd ~/tml26_task4
    git clone https://huggingface.co/datasets/SprintML/tml2026_task4 hf
    ```
6. Check the dataset folders are present and the clean target images has to be at `~/tml26_task4/hf/clean_targets/`
7. Place the script `freq_band_mix.py` and the precomputed candidates in `~/tml26_task4/`
8. Then run the final frequency band residual mixing script,

      ```     
   python freq_band_mix.py \
  --clean hf/clean_targets \
  --base combo_wm7blue_wm6_sota \
  --alt forged_spatial_a2.5_b41 \
  --wm 3 \
  --alpha 0.55 \
  --low 0.10 \
  --high 0.45 \
  --out freq_wm3_spatial_mid_a055 \
  --zip freq_wm3_spatial_mid_a055.zip
      ```
9. This will create, `freq_wm3_spatial_mid_a055/ and freq_wm3_spatial_mid_a055.zip`
10. Then edit the submission file `~/tml26_task4/hf/`, with `FILE_PATH = Path("/home/john/tml26_task4/freq_wm3_spatial_mid_a055.zip")`
11. Then run the commands,
    ```
    cd ~/tml26_task4/hf
    python submission.py
    ```
