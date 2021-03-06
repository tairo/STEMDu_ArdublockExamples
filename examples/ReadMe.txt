STEM Du / RDC-102 ArduBlock Examples

RDC-120/RDS-Xシリーズ用のArduBlockサンプルプログラムです。

・Arduinoで.inoファイルを先に開いてから、Arduinoのメニューのツール＞ArduBlockを選択します。
　ArduBlockの「開く（load）」ボタンを押して、.abpファイルを開きます。
・センサ／モータは、車体後ろから見て小さい番号が左側になるように配置するように作成してあります。
・STEM Duライブラリを使用します。STEM Du用のArduino IDE/ArduBlock環境を使用してください。

------------------------------------------------------------------------------------------------------------------------------
【crash-avoidance_sample1】

RDS-X12用のArduBlockサンプルプログラムです。

アナログ赤外線センサJES-7023を使用して障害物への衝突を回避します。
障害物の前で停止します。
JES-7023は赤外線LEDのスイッチをON側にしてアクティブで使用します。

使用コネクタ  A1 / Motor3 / Motor4

変数
ir1			JES-7023の出力値を格納します。

動作手順
・前方に障害物がなければ前進します。
・ir1の値がしきい値以上になったら停止します。
　しきい値は、ツール＞シリアルモニタを使ってir1の値を確認して設定します。
　シリアルモニタから表計算ソフトなどにコピー（ctrl+C）して数値を処理すると分かり易くなります。

※投射している赤外線に比較して周囲が明るいと前進と停止をしきい値で分けることができません。
　環境光の影響はJES-7023を変調赤外線を用いた測距センサRDI-209に置き換えることで改善されます。
※障害物が暗色の場合は、赤外線を吸収するため反応が悪くなります。
------------------------------------------------------------------------------------------------------------------------------
【crash-avoidance_sample2】

RDS-X12用のArduBlockサンプルプログラムです。

アナログ赤外線センサJES-7023を使用して障害物への衝突を回避します。
障害物の前で停止した後、方向を変えて再び前進します。
JES-7023は赤外線LEDのスイッチをON側にしてアクティブで使用します。

使用コネクタ  A1 / A2 / Motor3 / Motor4

変数
ir1, ir2		JES-7023の出力値を格納します。

動作手順
・前方に障害物がなければ前進します。
・ir1の値がしきい値以上になったら一時停止します。右折して、障害物がなければ再度前進します。
・ir2の値がしきい値以上になったら一時停止します。左折して、障害物がなければ再度前進します。
　しきい値は、ツール＞シリアルモニタを使ってir1、ir2の値を確認して設定します。
　サンプルはir1の出力になっていますので、ir2に書き換えてlUploadしてください。
　待ち時間は出力されません。
　シリアルモニタから表計算ソフトなどにコピー（ctrl+C）して数値を処理すると分かり易くなります。

※投射している赤外線に比較して周囲が明るいと前進と停止をしきい値で分けることができません。
　環境光の影響はJES-7023を変調赤外線を用いた測距センサRDI-209に置き換えることで改善されます。
※障害物が暗色の場合は、赤外線を吸収するため反応が悪くなります。
------------------------------------------------------------------------------------------------------------------------------
【crash-avoidance_sample3】※STEM Duライブラリを使用

crash-avoidance_sample1をSTEM Duライブラリを使用して書き直したものです。
------------------------------------------------------------------------------------------------------------------------------
【crash-avoidance_sample4】※STEM Duライブラリを使用

crash-avoidance_sample2をSTEM Duライブラリを使用して書き直したものです。
------------------------------------------------------------------------------------------------------------------------------
【base_floor_sample】

RDS-X13用のArduBlockサンプルプログラムです。

赤外線反射センサ　RDI-211を使用して床の明暗に反応して動きます。

使用コネクタ  A1 / A2 / Motor3 / Motor4

変数
ir1, ir2			RDI-211の出力値を格納します。

動作手順
・床の色が暗ければ前進します。
・ir1, ir2の値がしきい値以上になったら停止／旋回します。
　しきい値は、ツール＞シリアルモニタを使ってir1の値を確認して設定します。
　シリアルモニタから表計算ソフトなどにコピー（ctrl+C）して数値を処理すると分かり易くなります。
------------------------------------------------------------------------------------------------------------------------------
【base_ball_sample】

RDS-X13用のArduBlockサンプルプログラムです。

変調赤外線センサ　RDI-203JRを使用して赤外線ボールを探します。

使用コネクタ  A3 / A4 / Motor3 / Motor4

変数
pulse_ir1, pulse_ir2	RDI-203JRの出力値を格納します。

動作手順
・pulse_ir1がしきい値以下になったら左に旋回します。
・pulse_ir2がしきい値以下になったら右に旋回します。
・pulse_ir1, pulse_ir2ともに。しきい値以下になったら前進します。
・pulse_ir1, pulse_ir2ともに。しきい値以上の場合は右旋回でボールを探します。
　しきい値は、ツール＞シリアルモニタを使ってir1の値を確認して設定します。
　シリアルモニタから表計算ソフトなどにコピー（ctrl+C）して数値を処理すると分かり易くなります。
※RDI-203JRはボールの赤外線が強くなるほど出力が低くなりますので注意してください。
------------------------------------------------------------------------------------------------------------------------------
【base_floor_ball_sample】

RDS-X13用のArduBlockサンプルプログラムです。
「floor_sample」と「ball_sample」を組み合わせたプログラムです。

赤外線反射センサ　RDI-211および
変調赤外線センサ　RDI-203JRを使用して動きます。

使用コネクタ  A1 / A2 / A3 / A4 / Motor3 / Motor4

変数
ir1, ir2			RDI-211の出力値を格納します。
pulse_ir1, pulse_ir2	RDI-203JRの出力値を格納します。

動作手順
・ir1, ir2の値がしきい値以上になったら停止／旋回します。
・床の色が暗い場合は赤外線ボールを探します。
・pulse_ir1がしきい値以下になったら左に旋回します。
・pulse_ir2がしきい値以下になったら右に旋回します。
・pulse_ir1, pulse_ir2ともに。しきい値以下になったら前進します。
・pulse_ir1, pulse_ir2ともに。しきい値以上の場合は右旋回でボールを探します。
　しきい値は、ツール＞シリアルモニタを使ってir1の値を確認して設定します。
　シリアルモニタから表計算ソフトなどにコピー（ctrl+C）して数値を処理すると分かり易くなります。
※RDI-203JRはボールの赤外線が強くなるほど出力が低くなりますので注意してください。
------------------------------------------------------------------------------------------------------------------------------
【motor_slider】

RDC-102用のArduBlockサンプルプログラムです。

スライダーを動かすと、出力される値に応じてモータの回転数が変化します。
スライダーの出力は1024段階、モータのPWM出力設定は255段階ですので、
出力値を4で割った数値でスピードを設定します。

使用コネクタ／センサ	Motor1 / スライダー

変数
value	スライダーの出力値を格納します。

動作手順
・スライダーの値を変数Valueに格納します。
・シリアルにValueを1/4にしたPWM設定用の数値を出力します（シリアルモニタで確認できます）。
・モータブロックにモータ番号とPWM出力値を設定します。
・ずっと繰り返します。
------------------------------------------------------------------------------------------------------------------------------



