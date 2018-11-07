# 課題3レポート

　画像｢LLENN｣を原画像として用いる。この画像は縦841画素、横841画素である。

この画像を

ORG=imread('kirimichan.png'); % 原画像の入力  
ORG= rgb2gray(ORG); % カラー画像を白黒濃淡画像へ変換  
imagesc(ORG); colormap(gray); colorbar; % 画像の表示

によって読み込み、白黒濃淡画像へ変形して表示した結果を図1に示す。
