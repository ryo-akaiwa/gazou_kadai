# 課題６レポート

画像｢LLENN｣を原画像として用いる。この画像は縦841画素、横841画素である。

この原画像を図1に示す。

![原画像](https://github.com/ryo-akaiwa/gazou_kadai/blob/master/image06/LLENN.jpg?raw=true)  
図1　原画像

この画像を

ORG=imread('LLENN.jpg'); % 原画像の入力  
ORG = rgb2gray(ORG);  
imagesc(ORG); colormap(gray); colorbar; % 画像の表示

によって読み込み、グレースケール化して表示させた結果を図2に示す。

![原画像](https://github.com/ryo-akaiwa/gazou_kadai/blob/master/image06/kadai6_1.png?raw=true)
図2　グレースケール画像

次に、この図2の画像を

IMG = ORG>128; % 128による二値化  
imagesc(IMG); colormap(gray); colorbar; % 画像の表示

によって二値化画像にした結果を図3に示す。

![原画像](https://github.com/ryo-akaiwa/gazou_kadai/blob/master/image06/kadai6_2.png?raw=true)
図3　128ディザ法による二値化

また、図2の画像を

IMG = dither(ORG); % ディザ法による二値化  
imagesc(IMG); colormap(gray); colorbar; % 画像の表示

によって二値化した結果を図4に示す。

![原画像](https://github.com/ryo-akaiwa/gazou_kadai/blob/master/image06/kadai6_3.png?raw=true)
図4　ディザ法による二値化

このように図3の結果から、0から255までの値の半分の128で閾値を設定し、二値化したところ、グレースケールの画像を十分に再現していると思われる。  
また。ディザ法は、画像を小さいブロックに分け、そのブロック内の画素値とディザパターンの画素値を比較してその大小で白黒を決める方法である。小さいブロックごとに順に値をきめていくため、ディザ法の方が再現度が高いと思われる。  
他にも、ディザ法は毎回閾値が変化して行くため、図4のように白黒のみでも濃淡が表現されていると考えられる。
