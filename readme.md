# Machine learning workshop

## Instalace

Instalovat budeme následující věci:
- Anaconda (python + další balíčky, snadná instalace)
- Tensorflow
- CUDA, pokud máte vyhovující GPU
    - díky tomu budete učit na GPU, tedy rychleji

### CUDA
Pokud máte Nvidia GPU s compute capability => 3.5: 
- compute capability naleznete zde:
    https://developer.nvidia.com/cuda-gpus 
    (zde si rozklidněte pro váš typ, nejspíš CUDA-Enabled GeForce and TITAN Products)

tak můžete vše nainstalovat a bude to fungovat.

Pokud ne, jsou 3 možnosti:
- smířit se s tím, že budete používat jen CPU
- pro windows a compute capability 3.0 je možnost zde: 
https://medium.com/@naarkie/using-tensorflow-gpu-on-a-compute-3-0-graphics-card-in-windows-4184f4228fe9
- zkompilovat Tensorflow pro vaši (nižší) compute capability. 
    - pouze na vlastní nebezpečí, s tím vám moc neporadím
    - https://www.tensorflow.org/install/source
    - https://medium.com/@mccann.matt/compiling-tensorflow-with-cuda-3-0-support-42d8fe0bf3b5

### Instalace Anacondy
- Anaconda, python 3.7, https://www.anaconda.com/distribution/
    - windows: https://repo.anaconda.com/archive/Anaconda3-2019.07-Windows-x86_64.exe
    - linux: https://repo.anaconda.com/archive/Anaconda3-2019.07-Linux-x86_64.sh
    - MacOS: https://repo.anaconda.com/archive/Anaconda3-2019.07-MacOSX-x86_64.pkg 

### Instalace Tensorflow
- Po instalaci Anacondy otevřete příkazovou řádku a zadejte:
    - pokud máte vyhovující GPU:
        `conda install tensorflow-gpu`
    - pokud ne:
        `conda install tensorflow`    

- Nyní byste měli mít vše připraveno pro workshop.

### Pokud nemůžete najít compute capability:
Compute capability => 3.5:
- pro notebooky:
    - 2000 generace - vše
    - 1000 generace - vše 
    - 900, 900M generace - vše
    - 830M, 840M, 850M, 860M        
- pro desktopy:
    - 2000 generace - vše
    - 1000 generace - vše 
    - 900 generace - vše
    - GTX 780Ti, 780, 750Ti, 750
    - GT 705, 720, 730
Compute capability 3.0:
- pro notebooky:
    - 870M, 880M
    - GTX 700M generace - vše
    - GTX 600M generace - vše
    - GT 730M, 735M, 740M, 745M, 750M, 755M
    - GT 640M, 645M, 650M
- pro desktopy:
    - GTX 750, 760, 770
    - GTX 600 generace - vše
    
### Potřebné knihovny
stylegan: 
```
pip install moviepy
```
gpt-2:
```
pip install fire toposort
```

### Generování anime obličejů
StyleGAN repozitář: https://github.com/NVlabs/stylegan
Detailní návod: https://www.gwern.net/Faces

Stahněte si: https://github.com/NVlabs/stylegan/archive/master.zip
(nebo přes git, pokud s ním umíte)

Spuštěním `python pretrained_example.py` vygenerujete lidskou fotku.
Spuštěním `python pretrained_example_anime.py` vygenerujete anime obrázek.
Spuštěním `python pretrained_examples.py` vygenerujete 1000 anime obrázků.

### Generování textů

Vygenerování textu nepodmíněně
```
python src/generate_unconditional_samples.py --top_k 40 --temperature 0.9 --nsamples 2 --seed 0 --model_name monogatari
python src/generate_unconditional_samples.py --top_k 40 --temperature 0.9 --nsamples 2 --seed 0 --model_name naruto
python src/generate_unconditional_samples.py --top_k 40 --temperature 0.9 --nsamples 2 --seed 0 --model_name overlord
```

Podmíněné generování textu
```
python src/interactive_conditional_samples.py --top_k 40 --temperature 0.9  --seed 2000 --model_name monogatari
```
