# Python Audio Restoration Suite
A set of tools to restore audio quality from a variety of old analog sources, such as tape, cassettes, acetates and vinyl.

### Features
- Wow & Flutter Removal
- Speed matching to hum frequency
- EQ matching with differential EQ
- Sub-sample accurate Spectral Temporal Alignment
- Automatic Dropout Restoration
- Spectral Expander / Decompressor

### Installation
1) Install [uv](https://docs.astral.sh/uv/getting-started/installation/).
   - macOS and Linux:
     ```bash
     curl -LsSf https://astral.sh/uv/install.sh | sh
     ```
   - Windows (PowerShell):
     ```powershell
     powershell -ExecutionPolicy ByPass -c "irm https://astral.sh/uv/install.ps1 | iex"
     ```
   Open a new terminal afterwards so `uv` is on your `PATH`.

2) Download `pyaudiorestoration` and install its dependencies:
   ```bash
   git clone https://github.com/oulianov/pyaudiorestoration.git
   cd pyaudiorestoration
   uv sync
   ```
   uv installs Python 3.11 and the locked dependencies into `.venv`. You do not need to install Python yourself.

3) GPU acceleration: on macOS, [pytorch](https://pytorch.org/) is installed by default and spectrograms run on the Apple Silicon GPU (MPS). On Windows and Linux with an NVIDIA GPU, run `uv sync --extra torch` to install pytorch and massively speed up slow calculations; for CUDA builds, configure the matching PyTorch index as described in the [uv PyTorch guide](https://docs.astral.sh/uv/guides/integration/pytorch/).

4) In some cases, you have to troubleshoot the installation of some dependencies. Here is a list of known issues:
   - `freetype-py` may have trouble to downloading `freetype.dll`. In that case, download it from [FreeType](https://www.freetype.org/download.html) and place it in a folder included in your system's path.

### Starting a tool
Run a tool from inside the `pyaudiorestoration` folder with `uv run`, for example:
```bash
uv run pyrespeeder_gui.py
```

| Tool | Command |
| --- | --- |
| Wow & Flutter Removal | `uv run pyrespeeder_gui.py` |
| Speed matching to hum frequency | `uv run humspeed_gui.py` |
| EQ matching with differential EQ | `uv run difeq_gui.py` |
| Spectral Temporal Alignment | `uv run pytapesynch_gui.py` |
| Automatic Dropout Restoration (batch) | `uv run dropouts_gui.py` |
| Dropout Restoration (select on spectrogram) | `uv run dropout_healer_gui.py` |
| Spectral Expander / Decompressor | `uv run expander_gui.py` |
| Stereo panning | `uv run pypan_gui.py` |
| Renoiser | `uv run renoiser_gui.py` |


### How to Use
See the [wiki](https://github.com/HENDRIX-ZT2/pyaudiorestoration/wiki) for detailed instructions for the individual tools.
