# Zluda_Comfyui_Ollama

1.PYTHON:add pathにチェックを入れること
    2024.5.23 : Python 3.12.3
2.MINICONDA3 for Python 3.12
    2024.5.23 : conda 24.4.0

●ComfyUI
git clone https://github.com/comfyanonymous/ComfyUI.git
conda create -n comfyui python=3.10.6
conda activate comfyui
pip install torch-directml
pip install -r requirements.txt

プロンプトの文字見やすく
.comfy-multiline-input {
  font-family: "Fira Code";
  font-size: 12px;
}

batファイル作成
---
call conda activate comfyui

python main.py --directml --auto-launch --lowvram --disable-smart-memory
---
./custom_nodesにカスタムノードをインストール
ComfyUI Manager:git clone https://github.com/ltdrdata/ComfyUI-Manager.git
->ComfyUI-Custom-Scripts

ファイル保存場所
 %date:yy%%date:MM%%date:dd%/ComfyUI
とすると年月日フォルダにComfyUI_xxxxx.pngとして保存する

カスタムノード
 - Comfuyi Impact Pack(Face)
 - Comfyui Omspire pack
 - ComfyUI's ControlNet Auxiliary Preprocessors(Control Net)
 - Derfuu_ComfyUI_ModdedNodes(Text box)
 - WAS Node Suite(many kinds)
 - pythongosssss/ComfyUI-Custom-Scripts(many kinds)
 - FizzNodes(AnimatedDiff)
 - smZNodes(like stable diffusion)
 - AnimateDiff Evolved(AnimateDiff)
 - ComfyUI-VideoHelperSuite(img -> viedo)
 - Use Everywhere (UE Nodes) (wireless connection)
 - KJNodes for ComfyUI(visualise node)
 - comfyui-portrait-master
 - WD 1.4 tagger (img to txt)
 - rgthree 

●仮想環境の削除
conda remove -n "xxxxx" --all

●複数連番画像の動画化
  load images(upload)
  video combine

●before after
  手動でインストール
  cd %COMFYUI%\custom_nodes
  git clone https://github.com/rgthree/rgthree-comfy.git


●CONFYUI-ZLUDAのインストール

- VC(VC_redist.x64.exe)
- AMD-Software-PRO-Edition-23.Q4-Win10-Win11-For-HIP.exe
   Driverはインストールしない
   system pathに.....bin\を追加
再生はここから↓
- StableDiffusionは配下で git clone https://github.com/patientx/ComfyUI-Zluda
- 仮想環境 conda create -n zluda python=3.10.11  (3.10.11指定)
- conda activate zluda
- pip install -r requirements.txt
- pip uninstall torch torchvision -y
- pip install torch==2.3.0 torchvision --index-url https://download.pytorch.org/whl/cu118
- cd .\custom_nodes  git clone https://github.com/ltdrdata/ComfyUI-Manager.git
- git clone https://github.com/ltdrdata/ComfyUI-Impact-Pack.git
- cd ComfyUI-Impact-Pack
- git clone https://github.com/ltdrdata/ComfyUI-Impact-Subpack impact_subpack
- dllを配置
   curl -s -L https://github.com/lshqqytiger/ZLUDA/releases/download/rel.2804604c29b5fa36deca9ece219d3970b61d4c27/ZLUDA-windows-amd64.zip > zluda.zip
   zludaフォルダをComfyUI-Zluda配下に置く
   copy zluda\cublas.dll C:\user_data\miniconda3\envs\zluda\Lib\site-packages\torch\lib\cublas64_11.dll /y
   copy zluda\cusparse.dll C:\user_data\miniconda3\envs\zluda\Lib\site-packages\torch\lib\cusparse64_11.dll /y
   copy zluda\nvrtc.dll C:\user_data\miniconda3\envs\zluda\Lib\site-packages\torch\lib\nvrtc64_112_0.dll /y

●ollamaのインストール

- ollamaの0.1.34版が動作確認済
- ollamaインストールフォルダ(appData/local/programs/ollama)にzludaのcublas.dll->cublas64_11.dllで上書き


●rembg
conda create -n rembg   (Pythonは標準=最新)
pip install rembg[cli]
example;
  rembg i file_A file_B
  rembg p folder_A folder_B
