# 課題8レポート

　画像｢LLENN｣を原画像として用いる。この画像は縦841画素、横841画素である。

この原画像を図1に示す。

![原画像](https://github.com/ryo-akaiwa/gazou_kadai/blob/master/image08/LLENN.jpg?raw=true)
図1　原画像

この画像を

ORG = imread('LLENN.jpg'); % 画像の読み込み  
ORG = rgb2gray(ORG); % 白黒濃淡画像に変換  
imagesc(ORG); colormap(gray); colorbar; % 画像の表示

によって読み込み、白黒濃淡画像に変換し表示した結果を図2に示す。

![原画像](https://github.com/ryo-akaiwa/gazou_kadai/blob/master/image08/kadai8_1.jpg?raw=true)
図2　白黒濃淡画像

この画像を

IMG = ORG > 128; % 閾値128で二値化  
imagesc(IMG); colormap(gray); colorbar; % 画像の表示

と処理し、輝度値128で閾値を設定し、2値化した結果を図3に示す。

![原画像](https://github.com/ryo-akaiwa/gazou_kadai/blob/master/image08/kadai8_2.jpg?raw=true)
図3　閾値128で2値化した画像

また、この2値化した画像を

IMG = bwlabeln(IMG);  
imagesc(IMG); colormap(jet); colorbar; % 画像の表示

によってラベリングして表示したものを図4に示す。

![原画像](https://github.com/ryo-akaiwa/gazou_kadai/blob/master/image08/kadai8_3.jpg?raw=true)
図4　図3をラベリングした画像

この結果、この図3は多くの種類の色でラベリングされているため、図3は多くのまとまった領域つまり、連結成分によってこの画像が作られていることがわかる。
