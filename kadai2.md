# 課題2レポート

　標準画像｢LLENN｣を原画像として用いる。この画像を、

ORG=imread('Lenna.png'); % 原画像の入力  
ORG = rgb2gray(ORG); colormap(gray); colorbar;  
imagesc(ORG); axis image; % 画像の表示

によって読み込み、グレースケールで表示した結果を図1に示す。