# 課題2レポート

　標準画像｢LLENN｣を原画像として用いる。この画像は縦841画素、横841画素である。
この画像を  

ORG=imread('Lenna.png'); % 原画像の入力  
ORG = rgb2gray(ORG); colormap(gray); colorbar;  
imagesc(ORG); axis image; % 画像の表示

によって読み込み、グレースケールで表示した結果を図1に示す。

![原画像](https://github.com/ryo-akaiwa/gazou_kadai/blob/master/image02/kadai2_1.png?raw=true)  
図1 グレースケール

グレースケールは256階調で表現されているため、2階調画像を生成するには256/2の128の値で色の区別を付ければ良い。したがって、次のようの処理する。

IMG = ORG>128;  
imagesc(IMG); colormap(gray); colorbar;  axis image;

これによって生成した画像を図2に示す。

![原画像](https://github.com/ryo-akaiwa/gazou_kadai/blob/master/image02/kadai2_2.png?raw=true)
図2　2階調画像

また、4階調画像を生成するためには256/4から64が一つ色を区別する値としてあげられる。また、この64の倍数で色を区別することで、256を等間隔で分割し、これらの和をとることで1つの画像が生成される。
したがって、次のように処理する。

IMG0 = ORG>64;  
IMG1 = ORG>128;  
IMG2 = ORG>192;  
IMG = IMG0 + IMG1 + IMG2;  
imagesc(IMG); colormap(gray); colorbar;  axis image;

これによって生成した画像を図3に示す。

![原画像](https://github.com/ryo-akaiwa/gazou_kadai/blob/master/image02/kadai2_3.png?raw=true)
図3　4階調画像

また、8階調画像を生成するためには同じように256/8から32となり、この倍数で色を区別する。
したがって、次のように処理をする。

IMG0 = ORG>32;  
IMG1 = ORG>64;  
IMG2 = ORG>96;  
IMG3 = ORG>128;  
IMG4 = ORG>160;  
IMG5 = ORG>192;  
IMG6 = ORG>224;  
IMG = IMG0 + IMG1 + IMG2 + IMG3 + IMG4 + IMG5 + IMG6;  
imagesc(IMG); colormap(gray); colorbar;  axis image;

これによって生成した画像を図4に示す。
![原画像](https://github.com/ryo-akaiwa/gazou_kadai/blob/master/image02/kadai2_4.png?raw=true)
図4　8階調画像


このように等間隔に色を分け、組み合わせることで階調画像が出来ることが分かった。  
また、図4のキャラクターの顔や背景など濃度の境目で本体は存在しない輪郭があるように見える。これは疑似輪郭と呼ばれるもので、画像のディジタル化における画像劣化の原因となるものである。
