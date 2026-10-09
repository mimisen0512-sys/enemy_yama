# 菌尾の灰狼

灰色の二足狼と黄緑の菌類を融合した、正面向きのセルアニメ風素材です。
左右はキャラクター自身の左右です。尾は胴体に含まれ、単独では動きません。

## 素材

enemy_head.png / enemy_torso.png / enemy_left_arm.png / enemy_right_arm.png /
enemy_left_leg.png / enemy_right_leg.png は、それぞれ透明背景のRGBA PNGです。
enemy_preview.png は1536×1024の完成合成、enemy_parts_overview.png は確認用一覧です。
enemy_metadata.json に画像サイズ、配置、関節、描画順を収録しています。
validation_report.json は今回の画像・座標検証結果です。

## Godot 4での配置

各画像を同じフォルダでプロジェクトに取り込みます。Enemy(Node2D)を
キャンバス原点として、その下にTorsoPivot(Node2D)を作ります。
JSONのparts.torso.position_px + pivot_pxをTorsoPivot.positionに設定します。
Torso(Sprite2D)をTorsoPivotの子にし、centered=false、position=-pivot_pxにします。

残る5部位はTorsoPivotの子に各Pivot(Node2D)を作り、
positionをattach_points_px.torso_pivot_localに設定します。
その子のSprite2Dはcentered=false、position=-pivot_pxにし、対応PNGを割り当てます。
各Sprite2Dのz_indexはJSONの値、初期回転は0、スケールは(1,1)です。
Pivotを回すと、身体の接続点を中心に動きます。
JSONのrecommended_rotation_degreesは度単位なので、Godotではdeg_to_radで変換します。

## 検証と制約

6パーツ、RGBA、外側の透明、キャンバス内配置、関節座標の整合、JSONからの
完全な再合成を検証しました。推奨回転範囲の両端で、胴体と各部位の接続領域が
重なっていることも画像処理で検証しました。正面構図と瞳孔なしは目視確認済みです。
輪郭には通常のアンチエイリアスとして半透明画素があります。

画像生成の初案から分割素材を作る過程で輪郭や菌類の色に小さな差があります。
納品のenemy_preview.pngを最終デザインとしてください。
Godot実機上の描画・アニメーションは未検証です。大きな関節回転では
毛の重なりや輪郭の継ぎ目が見える可能性があり、推奨範囲は参考値です。
既存ゲームのコードやプロジェクト設定は変更していません。
