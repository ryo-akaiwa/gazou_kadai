# 課題3レポート

　画像｢LLENN｣を原画像として用いる。この画像は縦841画素、横841画素である。

この画像を

ORG=imread('kirimichan.png'); % 原画像の入力  
ORG= rgb2gray(ORG); % カラー画像を白黒濃淡画像へ変換  
imagesc(ORG); colormap(gray); colorbar; % 画像の表示

によって読み込み、白黒濃淡画像へ変形して表示した結果を図1に示す。

![原画像](https://github.com/ryo-akaiwa/gazou_kadai/blob/master/image03/kadai3_1.png?raw=true)
図1白黒濃淡画像

次に、輝度値が64以上の画素１、以外を0にするよに以下のように処理する。

IMG = ORG > 64; % 輝度値が64以上の画素を1，その他を0に変換  
imagesc(IMG); colormap(gray); colorbar;

これにより生成された画像を図2に示す。

![原画像](https://github.com/ryo-akaiwa/gazou_kadai/blob/master/image03/kadai3_2.png?raw=true)
図2　閾値が64のときの画像

また、輝度値が96以上の画素１、以外を0にするよに以下のように処理する。

IMG = ORG > 96;  
imagesc(IMG); colormap(gray); colorbar;

これにより生成された画像を図3に示す。

![原画像](https://github.com/ryo-akaiwa/gazou_kadai/blob/master/image03/kadai3_3.png?raw=true)
図3　閾値が96のときの画像

同じように閾値が128と192以上のときの処理を以下に示す。

IMG = ORG > 128;  
imagesc(IMG); colormap(gray); colorbar;

IMG = ORG > 192;  
imagesc(IMG); colormap(gray); colorbar;

これらの処理によって生成された画像を図4、図5に示す。

![原画像](https://github.com/ryo-akaiwa/gazou_kadai/blob/master/image03/kadai3_4.png?raw=true)
図4　閾値が128のときの画像

![原画像](https://github.com/ryo-akaiwa/gazou_kadai/blob/master/image03/kadai3_5.png?raw=true)
図5　閾値が192のときの画像

このように閾値が大きくなるにつれ黒色になる部分が広くなることが分かる。
また、閾値を適切な値に決めることで灰色が混ざった場合などでも輪郭をはっきり表せることが分かる。
