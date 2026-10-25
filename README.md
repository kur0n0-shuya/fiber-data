# 脳解剖アトラス 線維束データ（HCP1065 からの変換版）

アプリ「脳解剖アトラス」で表示している線維束データ。元データの CC BY-SA 4.0 に従い、同じライセンスで公開する。

## 出典

- Yeh F-C. Population-based tract-to-region connectome of the human brain and its hierarchical topology. *Nat Commun* 13, 4933 (2022). https://doi.org/10.1038/s41467-022-32595-4
- データ：HCP1065 tractography atlas（https://brain.labsolver.org/hcp_trk_atlas.html）
- Data were provided [in part] by the Human Connectome Project, WU-Minn Consortium (Principal Investigators: David Van Essen and Kamil Ugurbil; 1U54MH091657) funded by the 16 NIH Institutes and Centers that support the NIH Blueprint for Neuroscience Research; and by the McDonnell Center for Systems Neuroscience at Washington University.

## ライセンス

[Creative Commons Attribution-ShareAlike 4.0 International（CC BY-SA 4.0）](https://creativecommons.org/licenses/by-sa/4.0/)。全文は `LICENSE`。

HCP 由来のデータとして、WU-Minn HCP Open Access Data Use Terms（`HCP-DATA-USE-TERMS.txt`）の第1・2・3・5項にも従うこと（被験者の特定・接触をしない、利用時に謝辞を記載する等）。

## 元データからの変更

- 各線維束の流線を最大400本に間引いた（元の本数は `bundles.json` の `originalCount`）。
- 各流線を3点ごとに標本化した。
- 下記のバイナリ形式に変換した。

## 形式

- 座標系：ICBM152 nonlinear asymmetric 2009a、RAS+、単位 mm。
- `data/<ID>.bin`：リトルエンディアンの float32 の並び（x, y, z, x, y, z, …）。全流線の点をつなげたもの。
- `data/bundles.json`：各線維束の `id`、元ファイル（`source`）、元の本数・表示本数、`offsets`（各流線の開始点の番号。流線 s は点 `offsets[s]` から `offsets[s+1]-1` まで）。
- `data/<ID>.footprint.bin`：流線の端点付近の情報（float32）。アプリでの皮質表示用。
