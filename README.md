# fish-abm — 魚群ABMデモ集

エージェントベースモデル（ABM）による群れシミュレーションのブラウザデモ集。
すべてクライアントサイド（JavaScript）で動作し、サーバー計算はありません。

**▶ デモを見る: https://druk-drink.github.io/fish-abm/**

| デモ | モデル | 技術 |
|---|---|---|
| [Boids 2D（鳥）](https://druk-drink.github.io/fish-abm/boids2d.html) | Reynolds の3ルール＋捕食者＋秩序パラメータ可視化 | Canvas 2D |
| [Boids 3D（魚とサメ）](https://druk-drink.github.io/fish-abm/boids3d.html) | 3ルール＋トポロジカル近傍＋水流＋捕食者2種 | Three.js |
| [三宮モデル 2D](https://druk-drink.github.io/fish-abm/sannomiya2d.html) | 実魚実験パラメータの物理モデル。トラップ・flash expansion | Canvas 2D |
| [三宮×Boids 3D](https://druk-drink.github.io/fish-abm/sannomiya3d.html) | 三宮モデルの3D一般化。魚礁への蝟集 | Three.js |
| [流体相互作用ビューア](https://druk-drink.github.io/fish-abm/viewer.html) | ダイポール流体×視覚モデルの計算結果を3D再生 | Three.js |

## モデルの概要

- **Boids** (Reynolds 1987): 整列・結合・分離の3つの局所ルールから群れが創発する古典。
  近傍の定義は「半径R以内」（メトリック）と「近い順k個体」（トポロジカル、
  Ballerini et al. 2008 のムクドリ実測に基づく）を切替可能
- **三宮モデル** (三宮信夫, 水産工学 30(1), 1993, doi:10.18903/fisheng.30.1_41):
  質点力学による魚群の物理モデル。パラメータは実魚（タイリクバラタナゴ）の
  水槽実験から最小2乗推定された値をそのまま使用。障害物への反発だけでなく
  **誘引**を持つのが特徴で、定置網・魚礁まわりの行動を再現できる
- **流体相互作用モデル** (Filella et al. PRL 2018 系): 各魚をポテンシャル流の
  ダイポールとして扱い、魚が作る流れが他の魚を移流・回転させる。
  ビューアのデータは同モデルのPython実装による事前計算結果
  （視覚＋流体のみでミリング＝渦状態が創発する様子）

## ローカルで動かす

クローンして各HTMLをブラウザで開くだけです（ビルド不要）。
Three.jsはCDN（jsdelivr）から読み込むため、3D系デモは初回のみネット接続が必要です。

## 参考文献

- C. W. Reynolds, "Flocks, Herds, and Schools: A Distributed Behavioral Model", SIGGRAPH 1987
- M. Ballerini et al., "Interaction ruling animal collective behaviour depends on
  topological rather than metric distance", PNAS 2008
- 三宮信夫「魚群の行動モデルとシミュレーション」水産工学 Vol.30 No.1, pp.41-48, 1993
- A. Filella, F. Nadal, C. Sire, E. Kanso, C. Eloy,
  "Model of Collective Fish Behavior with Hydrodynamic Interactions", PRL 120, 198101, 2018

## License

MIT
