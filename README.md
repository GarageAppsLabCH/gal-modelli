# gal-modelli

[Italiano](#italiano) · [English](#english)

## Italiano

Modelli convertiti e qualificati delle app GAL di GarageAppsLab, che le app scaricano direttamente sul telefono.

### Che cos'è

Il repository contiene solo i modelli di intelligenza artificiale che le app GAL eseguono sul telefono, già convertiti per Core ML (iOS) e ncnn (Android) e qualificati dal Laboratorio GAL: licenza dei pesi verificata alla fonte, conversione controllata contro il modello d'origine. Non contiene il codice delle app né quello della conversione.

Le app scaricano i file da `raw.githubusercontent.com`, a un commit fissato nell'app e senza credenziali, e ne controllano l'integrità: l'impronta SHA-256 di `catalogo.json` è scritta nell'app e il catalogo porta l'impronta di ogni altro file.

### Contributi

Il repository è chiuso ai contributi esterni: issue, pull request, discussioni, wiki e progetti sono disattivati. Lo cura solo il Laboratorio GAL.

### Struttura

- `README.md`: questo file, con le tabelle dei modelli di ogni app.
- `<app>/<serie>/`: una serie di modelli di un'app, per esempio `stem-ai-studio/modelli-2/`, con:
  - `catalogo.json`: il catalogo della serie; per ogni modello identificativo, nome, licenza e attribuzione; per ogni piattaforma sistema minimo, file con byte e impronta SHA-256, memoria del modello, misurata o stimata;
  - `ios/`: modelli Core ML compilati, una cartella `<nome>.mlmodelc/` per modello;
  - `android/`: modelli ncnn, `<nome>.param` (struttura della rete) e `<nome>.bin` (pesi);
  - `licenze/`: testi delle licenze dei modelli, con le attribuzioni.
- File divisi: un file oltre 90 MiB è diviso in parti da 90 MiB, `<file>.part00`, `<file>.part01` e così via, perché GitHub non accetta file oltre 100 MB e il repository non usa Git LFS. Il file si ricompone concatenando le parti nell'ordine (`cat <file>.part* > <file>`); il catalogo dà byte e impronta di ogni parte e del file intero.

### Cartelle immutabili

Una serie pubblicata non cambia più: nessun suo file si modifica, si aggiunge o si toglie. Modelli nuovi o corretti vanno in una serie nuova (per esempio `modelli-3`), con il suo catalogo; si aggiorna solo questo README. Le app fissano commit e impronta del catalogo: una pubblicazione nuova non cambia un'app già distribuita.

### Licenze e verifica

Ogni modello ha la sua licenza, indicata nel catalogo e nelle tabelle qui sotto, con il testo integrale nella cartella `licenze/` della sua serie: chi usa un modello ne rispetta la licenza e ne riporta l'attribuzione. Per controllare un file: `shasum -a 256 <file>` (macOS) o `sha256sum <file>` (Linux), da confrontare con l'impronta del catalogo o delle tabelle.

## English

Converted and qualified models of the GAL apps by GarageAppsLab, downloaded by the apps directly to the phone.

### What it is

This repository holds only the AI models that the GAL apps run on the phone, already converted for Core ML (iOS) and ncnn (Android) and qualified by the GAL Laboratory: weight licences checked at the source, conversion checked against the original model. It holds neither the code of the apps nor the conversion code.

The apps download the files from `raw.githubusercontent.com`, at a commit pinned in the app and without credentials, and check their integrity: the SHA-256 hash of `catalogo.json` is written in the app, and the catalogue carries the hash of every other file.

### Contributions

The repository is closed to external contributions: issues, pull requests, discussions, wiki and projects are disabled. It is maintained only by the GAL Laboratory.

### Structure

- `README.md`: this file, with the model tables of each app.
- `<app>/<series>/`: one series of models of an app, for example `stem-ai-studio/modelli-2/`, with:
  - `catalogo.json`: the catalogue of the series; for each model its id, name, licence and attribution; for each platform the minimum system version, the files with bytes and SHA-256 hash, the memory of the model, measured or estimated;
  - `ios/`: compiled Core ML models, one `<name>.mlmodelc/` folder per model;
  - `android/`: ncnn models, `<name>.param` (network structure) and `<name>.bin` (weights);
  - `licenze/`: the licence texts of the models, with the attributions.
- Split files: a file larger than 90 MiB is split into 90 MiB parts, `<file>.part00`, `<file>.part01` and so on, because GitHub does not accept files over 100 MB and the repository does not use Git LFS. The file is rebuilt by joining the parts in order (`cat <file>.part* > <file>`); the catalogue gives the bytes and the hash of each part and of the whole file.

### Immutable folders

A published series never changes: none of its files is modified, added or removed. New or corrected models go into a new series (for example `modelli-3`) with its own catalogue; only this README is updated. The apps pin the commit and the catalogue hash: a new publication never changes an app already distributed.

### Licences and verification

Each model has its own licence, given in the catalogue and in the tables below, with the full text in the `licenze/` folder of its series: whoever uses a model follows its licence and keeps its attribution. To check a file: `shasum -a 256 <file>` (macOS) or `sha256sum <file>` (Linux), and compare it with the hash in the catalogue or in the tables.

## Modelli · Models

### Stem AI Studio · `stem-ai-studio/modelli-2`

Serie `modelli-2` di Stem AI Studio, l'app GAL che crea video karaoke sul telefono separando la voce dagli strumenti. · Series `modelli-2` of Stem AI Studio, the GAL app that makes karaoke videos on the phone by separating the vocals from the instruments.

- Catalogo · Catalogue: [`stem-ai-studio/modelli-2/catalogo.json`](stem-ai-studio/modelli-2/catalogo.json), SHA-256 `89fbb30d2c9d5750553e1e8cd5e2914f083dfbf088dd7bbe4054aa4ce6c29ea8`.
- File della serie · Files in the series: 53, 1418523545 byte (1352.8 MiB).
- Provenienza · Provenance: release `stem-ai-studio-modelli-2` del repository privato del Laboratorio GAL · of the GAL Laboratory's private repository, `GarageAppsLabCH/LABORATORIO_GAL` (più sotto · below).

| Modello · Model | id | Licenza · Licence | iOS | Android |
|---|---|---|---|---|
| Mel-Band RoFormer (Kimberley Jensen) | `mbr_kim` | MIT | 18.0+ · 930285230 byte | — |
| UVR-MDX-NET Kim Vocal 2 | `mdx_kim_vocal2` | MIT | 15.0+ · 66872015 byte | 7.0+ · 66742884 byte |
| UVR-MDX-NET Karaoke 2 | `mdx_kara2` | MIT | 15.0+ · 52899519 byte | 7.0+ · 52770402 byte |
| UVR-MDX-NET Karaoke 1 | `mdx_kara1` | MIT | 15.0+ · 29821004 byte | 7.0+ · 29691964 byte |
| UVR-MDX-NET Inst HQ 5 | `mdx_inst_hq5` | MIT | 15.0+ · 59187147 byte | 7.0+ · 59058020 byte |
| Open-Unmix UMX-HQ (vocals) | `umxhq_vocals` | MIT | 15.0+ · 35637233 byte | 7.0+ · 35531043 byte |

#### Mel-Band RoFormer (Kimberley Jensen) · `mbr_kim`

- Licenza · Licence: MIT, [`licenze/kim_models.txt`](stem-ai-studio/modelli-2/licenze/kim_models.txt).
- Attribuzione · Attribution: Kimberley Jensen (Mel-Band RoFormer vocal model, huggingface.co/KimberleyJSN/melbandroformer); Mel-Band RoFormer architecture by Ju-Chiang Wang, Wei-Tsung Lu and Minz Won (ByteDance AI Labs); network rewritten for the conversion following BS-RoFormer 0.3.10 by Phil Wang (MIT).
- iOS: Core ML, iOS 18.0+, `ios/mbr_kim.mlmodelc/`, 5 file, 930285230 byte (887.2 MiB).
  - Memoria · Memory: delta 2727 MB, stima prudente dopo la prova fallita sul telefono · prudent estimate after the failed phone test: massimo fra la stima · maximum of the estimate ⌈279 MB + 1.33 × 1840.6 MB⌉ = 2727 MB (misura_modelli.py: GitHub Actions macos-26, arm64, macchina virtuale senza GPU né Neural Engine, gal-modelli, run 43235336133, 2026-11-12; costo fisso · fixed cost b 279 MB, fattore · factor k 1.33, base · basis mdx_kim_vocal2, mdx_kara2, mdx_kara1, mdx_inst_hq5, umxhq_vocals) e il pavimento · and the floor 2464 MB (disponibile prima della prova di mdx_kim_vocal2 · available before the test of mdx_kim_vocal2); nel catalogo base 0 e picco = delta · in the catalogue baseline 0 and peak = delta. `source`: `telefono-fallito`. Prova sul telefono non riuscita · Phone test failed: memory: l'app si è chiusa durante la prova (2 volte, 09:11 e 09:15).
- Android: non pubblicato · not published.

Provenienza · Provenance (`provenienza.txt`):

```text
mbr_kim: Mel-Band RoFormer di Kimberley Jensen da https://huggingface.co/KimberleyJSN/melbandroformer/resolve/ac9b0614ab3cd7f77219e18ba494dfd93956c348/MelBandRoformer.ckpt (SHA-256 87201f4d31afb5bc79993230fc49446918425574db48c01c405e44f365c7559e)
  pesi MIT (scheda Hugging Face KimberleyJSN/melbandroformer, «license: mit» dalla revisione ac9b0614 del 22.04.2026; dichiarazione dell'autrice nell'issue #18 di KimberleyJensen/Mel-Band-Roformer-Vocal-Model); codice: riferimento BS-RoFormer 0.3.10 di Phil Wang (lucidrains, MIT) con rotary-embedding-torch (MIT), nucleo d'esportazione proprio in converti_modelli.py; nessun codice del repository dell'autrice
  riferimento: mask estimator di 2 strati nascosti (dalle chiavi), 684 chiavi caricate, 0 mancanti e 0 inattese; nucleo contro riferimento sull'audio del segnale di prova (STFT e iSTFT di torch): coseno 1.0000000 (soglia 0.9999)
  Core ML: ML Program iOS 18, pesi e calcolo float32; stft [1, 4, 1025, 801] -> vocals_stft
mbr_kim: ncnn non conforme (pezzo 3: 2.2 dB), non pubblicato per Android
  mbr_kim.rif: uscita di riferimento in float32, passo 51, 64395 valori float16
```

| Piattaforma · Platform | File | Byte | SHA-256 |
|---|---|--:|---|
| iOS | `ios/mbr_kim.mlmodelc/analytics/coremldata.bin` | 243 | `969003705f4338025de747eb03168b2ce6fc7cc5d5e3bbbfff7b4a4d16bd2fa2` |
| iOS | `ios/mbr_kim.mlmodelc/coremldata.bin` | 384 | `ca353012596084fc9287c55e2cac586daa27637d5ee82dc5476ecbd801035347` |
| iOS | `ios/mbr_kim.mlmodelc/metadata.json` | 2110 | `fdf6ff9c61be7b3a5082eea9f51a3a78b68d12436c9e8658391aa8e27ab158b0` |
| iOS | `ios/mbr_kim.mlmodelc/model.mil` | 781753 | `870ef4e3df939a3160ee61a71520d9df0abcc9f4e9b5f58622a8c440e9eb417f` |
| iOS | `ios/mbr_kim.mlmodelc/weights/weight.bin` (intero · whole) | 929500740 | `7b60ee1d01221a551fa27d2a9e40442c9170896ce97a0a35e8755531ad417f63` |
| iOS | ↳ `ios/mbr_kim.mlmodelc/weights/weight.bin.part00` | 94371840 | `991c1ad3fc3fb2b85d46fda6aeb117fca5efa5b875dc0ddd0f2cfb1c66a61fa2` |
| iOS | ↳ `ios/mbr_kim.mlmodelc/weights/weight.bin.part01` | 94371840 | `f50089f0e6ba783486a95fd63852a053d33b5b5803b9a1fddabd0f1054ea7628` |
| iOS | ↳ `ios/mbr_kim.mlmodelc/weights/weight.bin.part02` | 94371840 | `158536a5ae4191f98bd3b38f85eecad259ef7b15e8e212d28b5d956e037d113b` |
| iOS | ↳ `ios/mbr_kim.mlmodelc/weights/weight.bin.part03` | 94371840 | `3ec6d9585187b9c7338ffe5f5ca806b1da2fde73ae27c43fcb3ebebb092545a7` |
| iOS | ↳ `ios/mbr_kim.mlmodelc/weights/weight.bin.part04` | 94371840 | `d370ad668319d95cdc8c58a11f06eaba36a95564c7369ad770513212c72c7914` |
| iOS | ↳ `ios/mbr_kim.mlmodelc/weights/weight.bin.part05` | 94371840 | `b99f2c060623a92ecb14b519caafce49614ac3603c71680f04605acd18ad5691` |
| iOS | ↳ `ios/mbr_kim.mlmodelc/weights/weight.bin.part06` | 94371840 | `1ad0b25b0c3618b44a63dc32ce99b70b3961822bca27582397ebef7269996c77` |
| iOS | ↳ `ios/mbr_kim.mlmodelc/weights/weight.bin.part07` | 94371840 | `6f5c8156540f140b0f6ffa0020d1e917e9467745eb2316e19a658f9c6843e3c7` |
| iOS | ↳ `ios/mbr_kim.mlmodelc/weights/weight.bin.part08` | 94371840 | `efaba7c1ac068ae324d7cbe4a928c8b0c98dab24819ffd3df1bbb85f3272a36d` |
| iOS | ↳ `ios/mbr_kim.mlmodelc/weights/weight.bin.part09` | 80154180 | `27cec3a0be0a7f847ee09df5c84d69f4c122ef64b51bf183fc542380148e7ff9` |

#### UVR-MDX-NET Kim Vocal 2 · `mdx_kim_vocal2`

- Licenza · Licence: MIT, [`licenze/kim_models.txt`](stem-ai-studio/modelli-2/licenze/kim_models.txt).
- Attribuzione · Attribution: Kimberley Jensen (UVR-MDX-NET Kim Vocal 2, from the release all_public_uvr_models of github.com/TRvlvr/model_repo); MDX-Net architecture by Kuielab & Woosung Choi.
- iOS: Core ML, iOS 15.0+, `ios/Kim_Vocal_2.mlmodelc/`, 5 file, 66872015 byte (63.8 MiB).
  - Memoria · Memory: picco · peak 1742 MB, base · baseline 759 MB, delta 983 MB; misura sul telefono · phone measurement (iPhone 16 (A18, 6 core, RAM 7680 MB), build 1006, 2026-11-12). `source`: `telefono`. Misura CI della base della calibrazione · CI measurement in the calibration basis: delta 694.8 MB (GitHub Actions macos-26, arm64, macchina virtuale senza GPU né Neural Engine, gal-modelli, run 43235336133, 2026-11-12); (983 − 279) / 694.8 = 1.013.
- Android: ncnn, Android 7.0+, `android/Kim_Vocal_2.param`, `android/Kim_Vocal_2.bin`, 2 file, 66742884 byte (63.7 MiB).
  - Memoria · Memory: picco · peak 1943 MB, base · baseline 49.8 MB, delta 1893.2 MB; misura_modelli.py (GitHub Actions ubuntu-latest, x86_64, CPU, gal-modelli, run 43235336133, 2026-11-12). `source`: `ci`.

Provenienza · Provenance (`provenienza.txt`):

```text
Kim_Vocal_2: da https://github.com/TRvlvr/model_repo/releases/download/all_public_uvr_models/Kim_Vocal_2.onnx (SHA-256 ce74ef3b6a6024ce44211a07be9cf8bc6d87728cc852a68ab34eb8e58cde9c8b), con onnx2torch
  licenza dei pesi: MIT con uso commerciale, dichiarazioni dell'autrice Kimberley Jensen (issue #18 del repository Mel-Band-Roformer-Vocal-Model; issue #3 di kmdx-net)
  parametri da https://raw.githubusercontent.com/TRvlvr/application_data/3826b05b570dbd4fbedbc807758803b35348ba1b/mdx_model_data/model_data_new.json, chiave MD5 970b3f9492014d18fefeedfe4773cb42 (ultimi 10 240 000 byte del file, come UVR): dim_f 3072, n_fft 7680, hop 1024, dim_t 256, compensate 1.009, stem primario Vocals
  Core ML ML Program (iOS 15, float32) e ncnn (201 strati, pesi float32); input [1, 4, 3072, 256] -> output; ncnn contro PyTorch 122.2 dB (soglia 30)
  Kim_Vocal_2.rif: uscita di riferimento in float32, passo 48, 65536 valori float16
```

| Piattaforma · Platform | File | Byte | SHA-256 |
|---|---|--:|---|
| iOS | `ios/Kim_Vocal_2.mlmodelc/analytics/coremldata.bin` | 243 | `d039556d6ed4c9872cc5e23436310c73db43f4134ad8981885cb5d4d54a093bf` |
| iOS | `ios/Kim_Vocal_2.mlmodelc/coremldata.bin` | 380 | `6ba4fbcfce10bc3a7568e2bfde1a3ebcfe9227cc3127b2fac48e4bb5f01745fb` |
| iOS | `ios/Kim_Vocal_2.mlmodelc/metadata.json` | 1764 | `7af8516674baf20ebc37cf24c28478dbc67e7f98d2d073f97ae1af898798c74f` |
| iOS | `ios/Kim_Vocal_2.mlmodelc/model.mil` | 131452 | `71f9deb865bab852bd9a5130362862edd62c9d785cdefe34066777c148ce651e` |
| iOS | `ios/Kim_Vocal_2.mlmodelc/weights/weight.bin` | 66738176 | `ce9268da80a536955e9c183b12426e9b602490b11c95d09d23fae7edb56c870a` |
| Android | `android/Kim_Vocal_2.bin` | 66725660 | `dc125756b5b4dc1392a008135e36ba514b3f9e1c20b195b10f5a4e8b78c3aad3` |
| Android | `android/Kim_Vocal_2.param` | 17224 | `2f4640fab0eec6ac56714719f863570df8963aa2223da6706084df853aabb8c1` |

#### UVR-MDX-NET Karaoke 2 · `mdx_kara2`

- Licenza · Licence: MIT, [`licenze/uvr_models.txt`](stem-ai-studio/modelli-2/licenze/uvr_models.txt).
- Attribuzione · Attribution: Ultimate Vocal Remover (UVR) and its developers, Anjok07 and aufr33 (github.com/Anjok07/ultimatevocalremovergui; weights from the release all_public_uvr_models of github.com/TRvlvr/model_repo); MDX-Net architecture by Kuielab & Woosung Choi.
- iOS: Core ML, iOS 15.0+, `ios/UVR_MDXNET_KARA_2.mlmodelc/`, 5 file, 52899519 byte (50.4 MiB).
  - Memoria · Memory: picco · peak 1135 MB, base · baseline 351 MB, delta 784 MB; misura sul telefono · phone measurement (iPhone 16 (A18, 6 core, RAM 7680 MB), build 1006, 2026-11-12). `source`: `telefono`. Misura CI della base della calibrazione · CI measurement in the calibration basis: delta 480.5 MB (GitHub Actions macos-26, arm64, macchina virtuale senza GPU né Neural Engine, gal-modelli, run 43235336133, 2026-11-12); (784 − 279) / 480.5 = 1.051.
- Android: ncnn, Android 7.0+, `android/UVR_MDXNET_KARA_2.param`, `android/UVR_MDXNET_KARA_2.bin`, 2 file, 52770402 byte (50.3 MiB).
  - Memoria · Memory: picco · peak 1371.4 MB, base · baseline 49.9 MB, delta 1321.5 MB; misura_modelli.py (GitHub Actions ubuntu-latest, x86_64, CPU, gal-modelli, run 43235336133, 2026-11-12). `source`: `ci`.

Provenienza · Provenance (`provenienza.txt`):

```text
UVR_MDXNET_KARA_2: da https://github.com/TRvlvr/model_repo/releases/download/all_public_uvr_models/UVR_MDXNET_KARA_2.onnx (SHA-256 bf32e15105a09c0f7dddd2b67346146334d6f3ecb399ed7638eba2ab07cbf5f4), con onnx2torch
  licenza dei pesi: MIT, dichiarata dal progetto UVR per i suoi modelli (README di Anjok07/ultimatevocalremovergui, «License»: credito a UVR e ai suoi sviluppatori)
  parametri da https://raw.githubusercontent.com/TRvlvr/application_data/3826b05b570dbd4fbedbc807758803b35348ba1b/mdx_model_data/model_data_new.json, chiave MD5 1d64a6d2c30f709b8c9b4ce1366d96ee (ultimi 10 240 000 byte del file, come UVR): dim_f 2048, n_fft 5120, hop 1024, dim_t 256, compensate 1.065, stem primario Instrumental
  Core ML ML Program (iOS 15, float32) e ncnn (201 strati, pesi float32); input [1, 4, 2048, 256] -> output; ncnn contro PyTorch 120.3 dB (soglia 30)
  UVR_MDXNET_KARA_2.rif: uscita di riferimento in float32, passo 32, 65536 valori float16
```

| Piattaforma · Platform | File | Byte | SHA-256 |
|---|---|--:|---|
| iOS | `ios/UVR_MDXNET_KARA_2.mlmodelc/analytics/coremldata.bin` | 243 | `ec511e2b4c6fb7a47c300d4fc632700f7fe8069b50214a1b90f3bf3496bc0e8f` |
| iOS | `ios/UVR_MDXNET_KARA_2.mlmodelc/coremldata.bin` | 380 | `79d3d01f985109c83d46d67b1c1e2700348e664a2f64d5335c0dd4077cfa2556` |
| iOS | `ios/UVR_MDXNET_KARA_2.mlmodelc/metadata.json` | 1770 | `67d98620056afd4a796b0757a05fae273a9c1e32efd727660115ac25d1d18fd1` |
| iOS | `ios/UVR_MDXNET_KARA_2.mlmodelc/model.mil` | 131430 | `82e4ffc54c6ae178d377341e70224a5f72826e27754fef5efcc0c063d25c2193` |
| iOS | `ios/UVR_MDXNET_KARA_2.mlmodelc/weights/weight.bin` | 52765696 | `6a694fb4ef049463a79ccf58b508421464232be6ec27f00a185791c5e04a3dfb` |
| Android | `android/UVR_MDXNET_KARA_2.bin` | 52753180 | `274c5acfdf47cfb154a59b8408b0b506f210e09c50f3362b11cb4ce8a1ca66bc` |
| Android | `android/UVR_MDXNET_KARA_2.param` | 17222 | `2ec1f44652a93bcb4d803169b1ffdbe2c10bb49fdeea5e2c3c395a983480047c` |

#### UVR-MDX-NET Karaoke 1 · `mdx_kara1`

- Licenza · Licence: MIT, [`licenze/uvr_models.txt`](stem-ai-studio/modelli-2/licenze/uvr_models.txt).
- Attribuzione · Attribution: Ultimate Vocal Remover (UVR) and its developers, Anjok07 and aufr33 (github.com/Anjok07/ultimatevocalremovergui; weights from the release all_public_uvr_models of github.com/TRvlvr/model_repo); MDX-Net architecture by Kuielab & Woosung Choi.
- iOS: Core ML, iOS 15.0+, `ios/UVR_MDXNET_KARA.mlmodelc/`, 5 file, 29821004 byte (28.4 MiB).
  - Memoria · Memory: picco · peak 809 MB, base · baseline 122 MB, delta 687 MB; misura sul telefono · phone measurement (iPhone 16 (A18, 6 core, RAM 7680 MB), build 1006, 2026-11-12). `source`: `telefono`. Misura CI della base della calibrazione · CI measurement in the calibration basis: delta 332.9 MB (GitHub Actions macos-26, arm64, macchina virtuale senza GPU né Neural Engine, gal-modelli, run 43235336133, 2026-11-12); (687 − 279) / 332.9 = 1.226.
- Android: ncnn, Android 7.0+, `android/UVR_MDXNET_KARA.param`, `android/UVR_MDXNET_KARA.bin`, 2 file, 29691964 byte (28.3 MiB).
  - Memoria · Memory: picco · peak 929.8 MB, base · baseline 49.9 MB, delta 879.9 MB; misura_modelli.py (GitHub Actions ubuntu-latest, x86_64, CPU, gal-modelli, run 43235336133, 2026-11-12). `source`: `ci`.

Provenienza · Provenance (`provenienza.txt`):

```text
UVR_MDXNET_KARA: da https://github.com/TRvlvr/model_repo/releases/download/all_public_uvr_models/UVR_MDXNET_KARA.onnx (SHA-256 e3167c87333a48548413e972a286bf40bf5694001d2853861eb1435953f02d63), con onnx2torch
  licenza dei pesi: MIT, dichiarata dal progetto UVR per i suoi modelli (README di Anjok07/ultimatevocalremovergui, «License»: credito a UVR e ai suoi sviluppatori)
  parametri da https://raw.githubusercontent.com/TRvlvr/application_data/3826b05b570dbd4fbedbc807758803b35348ba1b/mdx_model_data/model_data_new.json, chiave MD5 2f5501189a2f6db6349916fabe8c90de (ultimi 10 240 000 byte del file, come UVR): dim_f 2048, n_fft 6144, hop 1024, dim_t 256, compensate 1.035, stem primario Vocals
  Core ML ML Program (iOS 15, float32) e ncnn (201 strati, pesi float32); input [1, 4, 2048, 256] -> output; ncnn contro PyTorch 115.4 dB (soglia 30)
  UVR_MDXNET_KARA.rif: uscita di riferimento in float32, passo 32, 65536 valori float16
```

| Piattaforma · Platform | File | Byte | SHA-256 |
|---|---|--:|---|
| iOS | `ios/UVR_MDXNET_KARA.mlmodelc/analytics/coremldata.bin` | 243 | `a88809ef27db45bee4205f5e263f62dc94e299c539a0b562e2316502509cd401` |
| iOS | `ios/UVR_MDXNET_KARA.mlmodelc/coremldata.bin` | 380 | `d2ce00ded03ae8017804ade667db2205f8721c08df667b4fa1a31279a7f9b5cc` |
| iOS | `ios/UVR_MDXNET_KARA.mlmodelc/metadata.json` | 1768 | `6bab4c35e2d65f3452af134cadef83f0808cac237bf0fa464ab97a78de48e6bf` |
| iOS | `ios/UVR_MDXNET_KARA.mlmodelc/model.mil` | 131317 | `2a9ac50762dea4d6845a933702f5f98532c38fbebd89ecd508c3c319954d7f33` |
| iOS | `ios/UVR_MDXNET_KARA.mlmodelc/weights/weight.bin` | 29687296 | `e00cabc07547ee0c0ece9fc7d27034b924c0c95e7385067f64f514857f5d07fe` |
| Android | `android/UVR_MDXNET_KARA.bin` | 29674780 | `36fbecce14effa3396303ca6b970a0e1d16f04ac72c1cb4b3cf753341a9d2b10` |
| Android | `android/UVR_MDXNET_KARA.param` | 17184 | `b997ad7a3468ba36d66623596b0080651a0cf8c51170945fdd49e6d2f9aeb8b5` |

#### UVR-MDX-NET Inst HQ 5 · `mdx_inst_hq5`

- Licenza · Licence: MIT, [`licenze/uvr_models.txt`](stem-ai-studio/modelli-2/licenze/uvr_models.txt).
- Attribuzione · Attribution: Ultimate Vocal Remover (UVR) and its developers, Anjok07 and aufr33 (github.com/Anjok07/ultimatevocalremovergui; weights from the release all_public_uvr_models of github.com/TRvlvr/model_repo); MDX-Net architecture by Kuielab & Woosung Choi.
- iOS: Core ML, iOS 15.0+, `ios/UVR-MDX-NET-Inst_HQ_5.mlmodelc/`, 5 file, 59187147 byte (56.4 MiB).
  - Memoria · Memory: picco · peak 1479 MB, base · baseline 467 MB, delta 1012 MB; misura sul telefono · phone measurement (iPhone 16 (A18, 6 core, RAM 7680 MB), build 1006, 2026-11-12). `source`: `telefono`. Misura CI della base della calibrazione · CI measurement in the calibration basis: delta 554 MB (GitHub Actions macos-26, arm64, macchina virtuale senza GPU né Neural Engine, gal-modelli, run 43235336133, 2026-11-12); (1012 − 279) / 554 = 1.323.
- Android: ncnn, Android 7.0+, `android/UVR-MDX-NET-Inst_HQ_5.param`, `android/UVR-MDX-NET-Inst_HQ_5.bin`, 2 file, 59058020 byte (56.3 MiB).
  - Memoria · Memory: picco · peak 1653.2 MB, base · baseline 49.8 MB, delta 1603.4 MB; misura_modelli.py (GitHub Actions ubuntu-latest, x86_64, CPU, gal-modelli, run 43235336133, 2026-11-12). `source`: `ci`.

Provenienza · Provenance (`provenienza.txt`):

```text
UVR-MDX-NET-Inst_HQ_5: da https://github.com/TRvlvr/model_repo/releases/download/all_public_uvr_models/UVR-MDX-NET-Inst_HQ_5.onnx (SHA-256 811cb24095d865763752310848b7ec86aeede0626cb05749ab35350e46897000), con onnx2torch
  licenza dei pesi: MIT, dichiarata dal progetto UVR per i suoi modelli (README di Anjok07/ultimatevocalremovergui, «License»: credito a UVR e ai suoi sviluppatori)
  parametri da https://raw.githubusercontent.com/TRvlvr/application_data/3826b05b570dbd4fbedbc807758803b35348ba1b/mdx_model_data/model_data_new.json, chiave MD5 cb790d0c913647ced70fc6b38f5bea1a (ultimi 10 240 000 byte del file, come UVR): dim_f 2560, n_fft 5120, hop 1024, dim_t 256, compensate 1.01, stem primario Instrumental
  Core ML ML Program (iOS 15, float32) e ncnn (201 strati, pesi float32); input [1, 4, 2560, 256] -> output; ncnn contro PyTorch 108.2 dB (soglia 30)
  UVR-MDX-NET-Inst_HQ_5.rif: uscita di riferimento in float32, passo 40, 65536 valori float16
```

| Piattaforma · Platform | File | Byte | SHA-256 |
|---|---|--:|---|
| iOS | `ios/UVR-MDX-NET-Inst_HQ_5.mlmodelc/analytics/coremldata.bin` | 243 | `a9bbe3a3fb2b149fad09ad1294eb1cd8fc152314108d88df6554768efaf38206` |
| iOS | `ios/UVR-MDX-NET-Inst_HQ_5.mlmodelc/coremldata.bin` | 380 | `905895a1973148fec31f6ea1e3a9cbaf29d2455c2023d69f1609da35ef3ca6ab` |
| iOS | `ios/UVR-MDX-NET-Inst_HQ_5.mlmodelc/metadata.json` | 1774 | `73f5c9b2e161341bc5467430c8ccad3a37b084555d2cc0abf20e4b77f3911367` |
| iOS | `ios/UVR-MDX-NET-Inst_HQ_5.mlmodelc/model.mil` | 131438 | `4ef8babd8409541c59af9da23ca46f97da2bfa910569c7b7e91ebcf3499f1dfc` |
| iOS | `ios/UVR-MDX-NET-Inst_HQ_5.mlmodelc/weights/weight.bin` | 59053312 | `a18a6b7b0c43cc744e2d3a56cbe10c633fcf34ec2115cc9db4183003d4ed4fcf` |
| Android | `android/UVR-MDX-NET-Inst_HQ_5.bin` | 59040796 | `42052b296c87e43fbdb969c821b948c57fbb0f4e8afbdee6798fff38c4a26b45` |
| Android | `android/UVR-MDX-NET-Inst_HQ_5.param` | 17224 | `ba9770f8d9138a8f6d9e2fe21b8048232fbac3e297a9e0bf84bdda9d2a20faf8` |

#### Open-Unmix UMX-HQ (vocals) · `umxhq_vocals`

- Licenza · Licence: MIT, [`licenze/open_unmix.txt`](stem-ai-studio/modelli-2/licenze/open_unmix.txt).
- Attribuzione · Attribution: Open-Unmix UMX-HQ 1.0.1 by Inria (Fabian-Robert Stöter, Antoine Liutkus), github.com/sigsep/open-unmix-pytorch, weights from Zenodo record 3370489.
- iOS: Core ML, iOS 15.0+, `ios/umxhq_vocals.mlmodelc/`, 5 file, 35637233 byte (34.0 MiB).
  - Memoria · Memory: picco · peak 299 MB, base · baseline 20 MB, delta 279 MB; misura sul telefono · phone measurement (iPhone 16 (A18, 6 core, RAM 7680 MB), build 1006, 2026-11-12). `source`: `telefono`. Misura CI della base della calibrazione · CI measurement in the calibration basis: delta 101.3 MB (GitHub Actions macos-26, arm64, macchina virtuale senza GPU né Neural Engine, gal-modelli, run 43235336133, 2026-11-12); 279 MB = b.
- Android: ncnn, Android 7.0+, `android/umxhq_vocals.param`, `android/umxhq_vocals.bin`, 2 file, 35531043 byte (33.9 MiB).
  - Memoria · Memory: picco · peak 191.2 MB, base · baseline 49.9 MB, delta 141.3 MB; misura_modelli.py (GitHub Actions ubuntu-latest, x86_64, CPU, gal-modelli, run 43235336133, 2026-11-12). `source`: `ci`.

Provenienza · Provenance (`provenienza.txt`):

```text
umxhq_vocals: Open-Unmix UMX-HQ, voce, da https://zenodo.org/records/3370489/files/vocals-b62c91ce.pth (SHA-256 b62c91cedbc7a066f1778ead5b5cecb377aa3a46a31af1cce7c5c8769339d083), openunmix 1.3.0
  licenza dei pesi: MIT (Open-Unmix, sigsep; Zenodo 3370489)
  Core ML ML Program (iOS 15, float32) e ncnn (36 strati, pesi float32, tracciato senza il lotto: Mat 3D come nel motore); mix_mag [1, 2, 2049, 512] -> vocals_mag; ncnn contro PyTorch 125.3 dB (soglia 30)
  umxhq_vocals.rif: uscita di riferimento in float32, passo 33, 63582 valori float16
```

| Piattaforma · Platform | File | Byte | SHA-256 |
|---|---|--:|---|
| iOS | `ios/umxhq_vocals.mlmodelc/analytics/coremldata.bin` | 243 | `b9bb8da330f1cc260d84a128835f2aeb8265a37ad8e205412c3ef9134781e247` |
| iOS | `ios/umxhq_vocals.mlmodelc/coremldata.bin` | 386 | `a6198a16406fc1b3470f3442256a7c570df0e2f87de89f8599854608911abda6` |
| iOS | `ios/umxhq_vocals.mlmodelc/metadata.json` | 1869 | `eeb299693afe616b7e440ea1330adc357ede4af38120f0ac5c8b8b0253b28f97` |
| iOS | `ios/umxhq_vocals.mlmodelc/model.mil` | 21479 | `be6239dc6bbb423c2a1474da887666f2ba862e837f84405cbfcf6face51848c9` |
| iOS | `ios/umxhq_vocals.mlmodelc/weights/weight.bin` | 35613256 | `212ba9e24c1e37d1a1d53312f797cc44bdcf93b77a2dafe474826248bff07c15` |
| Android | `android/umxhq_vocals.bin` | 35528388 | `f516714147a1e7f045fe1043a6bdfc7278d5142d41a76a483fa84a491c2a6568` |
| Android | `android/umxhq_vocals.param` | 2655 | `dc575382d4c931f3adecb85a5ca785017537b2262b7a29566b0a9fbc8bb57f5d` |

#### Misura della memoria · Memory measurement

Valori in MB di 2^20 byte · Values in MB of 2^20 bytes. Picco · peak: massimo della memoria del processo durante la misura · maximum of the process memory during the measurement. Base · baseline: la parte che non è del modello · the part that does not belong to the model. Delta = picco − base · peak − baseline: la memoria del modello in uso, da cui l'app ricava il fabbisogno, con un margine, e lo confronta con la memoria che il telefono le concede · the memory taken by the model while running, from which the app derives its need, with a margin, and compares it with the memory the phone grants it.

Regole del catalogo per piattaforma, nella chiave `source` di `memory` · Catalogue rules per platform, in the `source` key of `memory`:

1. `telefono`: la misura sul telefono riuscita, che ha la precedenza · the successful phone measurement, which comes first.
2. `ci-calibrata` e `ci`: la misura di `misura_modelli.py`, con un modello lineare prudente. La base sono i modelli con le due misure: b, il delta sul telefono più piccolo fra loro, è il costo fisso (memoria di base dell'app e costi fissi del runtime, che il delta sul telefono di ogni modello comprende); k è il massimo di (delta sul telefono − b) / delta di `misura_modelli.py` sugli altri modelli della base, arrotondato per eccesso a due decimali. Un modello con la sola misura di `misura_modelli.py` ha delta = ⌈b + k × delta di `misura_modelli.py`⌉ (`ci-calibrata`). Con un solo modello nella base, o nessuno oltre b, b = 0 e k è il massimo dei rapporti delta sul telefono / delta di `misura_modelli.py` (regola del rapporto); se nessun modello della piattaforma ha le due misure, il delta com'è (`ci`). Su iOS `misura_modelli.py` misura Core ML sulla sola CPU (runner macOS di GitHub Actions, senza GPU né Neural Engine), mentre sul telefono Core ML usa la GPU, con molta più memoria e costi fissi che pesano soprattutto nei modelli piccoli: per questo b si toglie prima del rapporto · `ci-calibrata` and `ci`: the `misura_modelli.py` measurement, with a prudent linear model. The basis is the models with both measurements: b, the smallest phone delta among them, is the fixed cost (the app's baseline memory and the fixed costs of the runtime, included in the phone delta of every model); k is the largest (phone delta − b) / `misura_modelli.py` delta over the other models of the basis, rounded up to two decimals. A model with only the `misura_modelli.py` measurement gets delta = ⌈b + k × `misura_modelli.py` delta⌉ (`ci-calibrata`). With only one model in the basis, or none above b, b = 0 and k is the largest ratio phone delta / `misura_modelli.py` delta (ratio rule); when no model of the platform has both measurements, the delta as is (`ci`). On iOS `misura_modelli.py` measures Core ML on the CPU only (GitHub Actions macOS runners, without GPU or Neural Engine), while on the phone Core ML uses the GPU, with much more memory and fixed costs that weigh most on the small models: this is why b is taken off before the ratio.
3. `telefono-fallito`: un modello che nella prova sul telefono ha chiuso l'app per memoria ha delta = massimo fra la stima della regola 2, se c'è, e il pavimento, la memoria disponibile più bassa fra quella all'inizio delle prove e quella prima di ogni prova riuscita che lo precede. Le prove vanno dal modello più leggero al più pesante nello stesso processo e la memoria disponibile cala, quindi il modello ha chiuso l'app con al più quella memoria disponibile. È una regola prudente, non una misura · `telefono-fallito`: a model that closed the app for lack of memory in the phone test gets delta = the maximum of the estimate of rule 2, if any, and the floor, the lowest memory available at the start of the tests or before any successful test that precedes it. The tests run from the lightest model to the heaviest in one process and the available memory only goes down, so the model closed the app with at most that memory available. It is a prudent rule, not a measurement.
4. `memory` null: nessuna misura né stima, l'app stima il fabbisogno dai pesi · no measurement or estimate, the app estimates its need from the weights.

Nelle stime (`ci-calibrata`, `telefono-fallito`) non c'è una misura del processo: nel catalogo base 0 e picco = delta; `factor` (k), `baseMb` (b, dentro il delta, non è `baselineMb`), `basis`, `ciDeltaMb`, `estimateMb` e `floorMb` dicono da dove viene il valore, `device` e `measured` il telefono delle misure · In the estimates (`ci-calibrata`, `telefono-fallito`) there is no process measurement: in the catalogue baseline 0 and peak = delta; `factor` (k), `baseMb` (b, inside the delta, not `baselineMb`), `basis`, `ciDeltaMb`, `estimateMb` and `floorMb` tell where the value comes from, `device` and `measured` the phone of the measurements.

- **Telefono · Phone, iOS**: iPhone 16 (A18, 6 core, RAM 7680 MB), build 1006, 2026-11-12. Core ML, unità ALL (GPU e CPU per i modelli float32). Memoria disponibile all'app all'inizio · memory available to the app at the start: 3223 MB. Prova del motore dell'app per ogni modello, in sequenza nello stesso processo dal più leggero al più pesante: picco = massimo della memoria del processo (phys_footprint, ogni 20 ms durante il caricamento e tre esecuzioni); base = memoria trattenuta dalle prove precedenti (disponibile all'inizio − disponibile prima della prova, os_proc_available_memory); il delta comprende ancora la memoria di base dell'app, quindi la stima è prudente. · The app engine's test of each model, in sequence in one process from the lightest to the heaviest: peak = maximum of the process memory (phys_footprint, sampled every 20 ms during loading and three runs); baseline = memory retained by the earlier tests (available at the start − available before the test, os_proc_available_memory); the delta still includes the app's own baseline memory, so the estimate is prudent.
- **misura_modelli.py, Android**: GitHub Actions ubuntu-latest, x86_64, CPU; gal-modelli, run 43235336133, 2026-11-12; Python 3.12.16, ncnn 1.0.20261020, Linux-7.0.0-1017-azure-x86_64-with-glibc2.39. ncnn sulla CPU senza Vulkan, float32, 2 thread · ncnn on the CPU without Vulkan, float32, 2 thread. Un processo a sé per modello: base = memoria del processo dopo le importazioni, prima di ingresso e caricamento; picco = massimo del processo (VmRSS/VmHWM) dopo il caricamento e 2 esecuzioni su un ingresso della forma reale. · One process per model: baseline = process memory after the imports, before the input and the loading; peak = process maximum (VmRSS/VmHWM) after the loading and 2 runs on an input of the real shape.
- **misura_modelli.py, iOS**: GitHub Actions macos-26, arm64, macchina virtuale senza GPU né Neural Engine; gal-modelli, run 43235336133, 2026-11-12; Python 3.12.10, coremltools 9.0, macOS-26.7.2-arm64-arm-64bit. Core ML, unità di calcolo ALL · Core ML, ALL compute units. Un processo a sé per modello: base = memoria del processo dopo le importazioni, prima di ingresso e caricamento; picco = massimo del processo (ru_maxrss) dopo il caricamento e 2 esecuzioni su un ingresso della forma reale. · One process per model: baseline = process memory after the imports, before the input and the loading; peak = process maximum (ru_maxrss) after the loading and 2 runs on an input of the real shape.
- **Calibrazione · Calibration, iOS**: delta stimato = ⌈b + k × delta di `misura_modelli.py`⌉ · estimated delta = ⌈b + k × `misura_modelli.py` delta⌉; b = 279 MB, costo fisso, il delta sul telefono più piccolo della base (`umxhq_vocals`); k = 1.33, il massimo di (delta sul telefono − b) / delta di `misura_modelli.py` sugli altri modelli della base, arrotondato per eccesso a due decimali · b = 279 MB, fixed cost, the smallest phone delta of the basis (`umxhq_vocals`); k = 1.33, the largest (phone delta − b) / `misura_modelli.py` delta over the other models of the basis, rounded up to two decimals. Base · Basis: `mdx_kim_vocal2` (983 − 279) / 694.8 = 1.013, `mdx_kara2` (784 − 279) / 480.5 = 1.051, `mdx_kara1` (687 − 279) / 332.9 = 1.226, `mdx_inst_hq5` (1012 − 279) / 554 = 1.323, `umxhq_vocals` 279 MB = b.

#### Provenienza · Provenance

Asset della release `stem-ai-studio-modelli-2` di `GarageAppsLabCH/LABORATORIO_GAL`, controllati su `SHA256SUMS` e sulle impronte fissate nello script di pubblicazione · Assets of the release `stem-ai-studio-modelli-2` of `GarageAppsLabCH/LABORATORIO_GAL`, checked against `SHA256SUMS` and the hashes pinned in the publishing script:

| Asset | Byte | SHA-256 | Nella serie · In the series |
|---|--:|---|---|
| `Kim_Vocal_2.bin` | 66725660 | `dc125756b5b4dc1392a008135e36ba514b3f9e1c20b195b10f5a4e8b78c3aad3` | `android/Kim_Vocal_2.bin` |
| `Kim_Vocal_2.mlmodelc.zip` | 62063555 | `ad2b562a4e3d5533079cce82ae72596ce17918ebc5e7bf4a6214f8be3b616e55` | `ios/Kim_Vocal_2.mlmodelc/` |
| `Kim_Vocal_2.param` | 17224 | `2f4640fab0eec6ac56714719f863570df8963aa2223da6706084df853aabb8c1` | `android/Kim_Vocal_2.param` |
| `SHA256SUMS` | 1944 | `1ef808e2ba89257cd6db665a0dfb7a24b324bd2f948d523fecd917bef2f6eed6` | — |
| `UVR-MDX-NET-Inst_HQ_5.bin` | 59040796 | `42052b296c87e43fbdb969c821b948c57fbb0f4e8afbdee6798fff38c4a26b45` | `android/UVR-MDX-NET-Inst_HQ_5.bin` |
| `UVR-MDX-NET-Inst_HQ_5.mlmodelc.zip` | 54891998 | `d899305b5978b1dc680e45e41074bee489038b136076db1be949b076de60b97c` | `ios/UVR-MDX-NET-Inst_HQ_5.mlmodelc/` |
| `UVR-MDX-NET-Inst_HQ_5.param` | 17224 | `ba9770f8d9138a8f6d9e2fe21b8048232fbac3e297a9e0bf84bdda9d2a20faf8` | `android/UVR-MDX-NET-Inst_HQ_5.param` |
| `UVR_MDXNET_KARA.bin` | 29674780 | `36fbecce14effa3396303ca6b970a0e1d16f04ac72c1cb4b3cf753341a9d2b10` | `android/UVR_MDXNET_KARA.bin` |
| `UVR_MDXNET_KARA.mlmodelc.zip` | 27543773 | `9ef8f46597fc55ca07fb16a9195bd8a2a7b68b4ca9c63780e4bbd91603f6d509` | `ios/UVR_MDXNET_KARA.mlmodelc/` |
| `UVR_MDXNET_KARA.param` | 17184 | `b997ad7a3468ba36d66623596b0080651a0cf8c51170945fdd49e6d2f9aeb8b5` | `android/UVR_MDXNET_KARA.param` |
| `UVR_MDXNET_KARA_2.bin` | 52753180 | `274c5acfdf47cfb154a59b8408b0b506f210e09c50f3362b11cb4ce8a1ca66bc` | `android/UVR_MDXNET_KARA_2.bin` |
| `UVR_MDXNET_KARA_2.mlmodelc.zip` | 49027821 | `2a9d6d9544413284bc2ce5a60314d3f4e14845f57344b4d5b5255757c2dc616b` | `ios/UVR_MDXNET_KARA_2.mlmodelc/` |
| `UVR_MDXNET_KARA_2.param` | 17222 | `2ec1f44652a93bcb4d803169b1ffdbe2c10bb49fdeea5e2c3c395a983480047c` | `android/UVR_MDXNET_KARA_2.param` |
| `mbr_kim.mlmodelc.zip` | 847858620 | `eaafcce3620248fb7b654d2acccfe7119f635225f9075f73d5a8f4b00b293f3c` | `ios/mbr_kim.mlmodelc/` |
| `provenienza.txt` | 10155 | `b947d06a43fe9826cdbcb3dc6acf69cf08cc683ea10323441afb90fad71defcb` | questo README · this README |
| `umxhq_vocals.bin` | 35528388 | `f516714147a1e7f045fe1043a6bdfc7278d5142d41a76a483fa84a491c2a6568` | `android/umxhq_vocals.bin` |
| `umxhq_vocals.mlmodelc.zip` | 33434488 | `cf2d7be0426e803ec2db07a89b38c93c73a6d66bc2108ffc7b4f8d849ddaeebd` | `ios/umxhq_vocals.mlmodelc/` |
| `umxhq_vocals.param` | 2655 | `dc575382d4c931f3adecb85a5ca785017537b2262b7a29566b0a9fbc8bb57f5d` | `android/umxhq_vocals.param` |

Non pubblicati · Not published: `Kim_Vocal_2.rif`, `UVR-MDX-NET-Inst_HQ_5.rif`, `UVR_MDXNET_KARA.rif`, `UVR_MDXNET_KARA_2.rif`, `mbr_kim.rif`, `umxhq_vocals.rif` (uscite di riferimento della conversione, non usate dalle app · conversion reference outputs, not used by the apps).

Conversione · Conversion (`provenienza.txt`, righe generali · general lines):

```text
Stem AI Studio — modelli del motore convertiti da tool/converti_modelli.sh: Core ML (iOS), ncnn (Android) e uscite di riferimento .rif della prova sul telefono
Python 3.12.16; torch 2.5.1+cpu, torchaudio 2.5.1+cpu, torchvision 0.20.1+cpu, numpy 1.26.4, onnx 1.17.0, onnx2torch 1.5.15, coremltools 9.0, pnnx 20261020, ncnn 1.0.20261020, BS-RoFormer 0.3.10, rotary-embedding-torch 0.5.3, einops 0.8.1, beartype 0.19.0, librosa 0.10.2.post1, openunmix 1.3.0
Segnale di prova dei .rif: SPEC R04 §5 (8 s sintetici, 44100 Hz, stereo; rumore xorshift32 da 0x9E3779B9); ingressi costruiti con torch.stft (Hann periodica, center, riflessione) come nel motore
File prodotti (SHA-256):
  coreml/Kim_Vocal_2.mlpackage/Manifest.json 7b66da63eba2895169df1db233008055557536bb29d4c9a7d12f2f37ee31e42c
  coreml/Kim_Vocal_2.mlpackage/Data/com.apple.CoreML/model.mlmodel 9ba77dab7901122be978ebb3f458e0e6c66381c84db6c1cdaf1f0235cf80bbd1
  coreml/Kim_Vocal_2.mlpackage/Data/com.apple.CoreML/weights/weight.bin ce9268da80a536955e9c183b12426e9b602490b11c95d09d23fae7edb56c870a
  coreml/UVR-MDX-NET-Inst_HQ_5.mlpackage/Manifest.json b1c8c4bed566be814ea3bcb42237fadeaffbe97c360d5d114629ef8f10d6c2eb
  coreml/UVR-MDX-NET-Inst_HQ_5.mlpackage/Data/com.apple.CoreML/model.mlmodel da1ddb12d19f5a30fd3c189d649dffd3b9493de5c2901086acd9596942b7d2f2
  coreml/UVR-MDX-NET-Inst_HQ_5.mlpackage/Data/com.apple.CoreML/weights/weight.bin a18a6b7b0c43cc744e2d3a56cbe10c633fcf34ec2115cc9db4183003d4ed4fcf
  coreml/UVR_MDXNET_KARA.mlpackage/Manifest.json ad65a9782b96a34da62761faf1a60b95ab13c6e15069af6e9023c48907596079
  coreml/UVR_MDXNET_KARA.mlpackage/Data/com.apple.CoreML/model.mlmodel 1e69a31633fd69bbfcd371cbc39501f852a535564bc013f63d6e1d1938c3bd65
  coreml/UVR_MDXNET_KARA.mlpackage/Data/com.apple.CoreML/weights/weight.bin e00cabc07547ee0c0ece9fc7d27034b924c0c95e7385067f64f514857f5d07fe
  coreml/UVR_MDXNET_KARA_2.mlpackage/Manifest.json 58f4c28c82b84adf42f52f2a021678b608ca5198eecccd9ba5dd566df46d2328
  coreml/UVR_MDXNET_KARA_2.mlpackage/Data/com.apple.CoreML/model.mlmodel 966a22bf0c09ec389ab58d8f4e18fa63cb20a9cd1c4eef96d1568a1299ded1d1
  coreml/UVR_MDXNET_KARA_2.mlpackage/Data/com.apple.CoreML/weights/weight.bin 6a694fb4ef049463a79ccf58b508421464232be6ec27f00a185791c5e04a3dfb
  coreml/mbr_kim.mlpackage/Manifest.json abd94e1e00670cbba013a0752ea0e9c0601d1ef2e039e5535ab4576d0f711b55
  coreml/mbr_kim.mlpackage/Data/com.apple.CoreML/model.mlmodel 697458c32e3523677d67c5fd84e1966fcbc54618ec49b583edaac1a7e3baa8c8
  coreml/mbr_kim.mlpackage/Data/com.apple.CoreML/weights/weight.bin 7b60ee1d01221a551fa27d2a9e40442c9170896ce97a0a35e8755531ad417f63
  coreml/umxhq_vocals.mlpackage/Manifest.json 7e8aace3a994010bf63d73700522f70a5564748a9f00760a028e498d3f148749
  coreml/umxhq_vocals.mlpackage/Data/com.apple.CoreML/model.mlmodel d8b0e9b737c88ab6bd49fc5632bcab99e4e6ddf4638f199b71bafcef0ca523a8
  coreml/umxhq_vocals.mlpackage/Data/com.apple.CoreML/weights/weight.bin 212ba9e24c1e37d1a1d53312f797cc44bdcf93b77a2dafe474826248bff07c15
  ncnn/Kim_Vocal_2.bin dc125756b5b4dc1392a008135e36ba514b3f9e1c20b195b10f5a4e8b78c3aad3
  ncnn/Kim_Vocal_2.param 2f4640fab0eec6ac56714719f863570df8963aa2223da6706084df853aabb8c1
  ncnn/Kim_Vocal_2.rif 3f72228c15ff68b0e11cf178359b6f1cf4b1f75a3a0617a8ba60874b0a68c7fa
  ncnn/UVR-MDX-NET-Inst_HQ_5.bin 42052b296c87e43fbdb969c821b948c57fbb0f4e8afbdee6798fff38c4a26b45
  ncnn/UVR-MDX-NET-Inst_HQ_5.param ba9770f8d9138a8f6d9e2fe21b8048232fbac3e297a9e0bf84bdda9d2a20faf8
  ncnn/UVR-MDX-NET-Inst_HQ_5.rif c6c2b92e2f0cae820128744c682db3b367359342cfcde243fbefceea2cd99fd0
  ncnn/UVR_MDXNET_KARA.bin 36fbecce14effa3396303ca6b970a0e1d16f04ac72c1cb4b3cf753341a9d2b10
  ncnn/UVR_MDXNET_KARA.param b997ad7a3468ba36d66623596b0080651a0cf8c51170945fdd49e6d2f9aeb8b5
  ncnn/UVR_MDXNET_KARA.rif 58a4563d8f8d394f524ffcbfc60d885b7f6dd1ca3288603cf0e5897c8db1170d
  ncnn/UVR_MDXNET_KARA_2.bin 274c5acfdf47cfb154a59b8408b0b506f210e09c50f3362b11cb4ce8a1ca66bc
  ncnn/UVR_MDXNET_KARA_2.param 2ec1f44652a93bcb4d803169b1ffdbe2c10bb49fdeea5e2c3c395a983480047c
  ncnn/UVR_MDXNET_KARA_2.rif ecbfd280dcaf4f1a4c6b89570a355baad886edb3643ae8246e1a04b804146e9d
  ncnn/mbr_kim.rif 123dc5fa5e2913a8a1c30f05d02cc861606defc27a6c402e05f481cb714fc813
  ncnn/umxhq_vocals.bin f516714147a1e7f045fe1043a6bdfc7278d5142d41a76a483fa84a491c2a6568
  ncnn/umxhq_vocals.param dc575382d4c931f3adecb85a5ca785017537b2262b7a29566b0a9fbc8bb57f5d
  ncnn/umxhq_vocals.rif c2080764a8929d84d056999460cdefdf5563eed0c8aa41f5679e4dac9bceb183
ncnn-20261020-android.zip (tool/prepare_models.sh, Android): da https://github.com/Tencent/ncnn/releases/download/20261020/ncnn-20261020-android.zip, SHA-256 62a9edb493ceb42a5c9cbf2d3a79b3f44bff06c625134ffb64d183dcc42c25fc
```
