# 課題5レポート

画像｢LLENN｣を原画像として用いる。この画像は縦841画素、横841画素である。

この原画像を図1に示す。

![原画像](https://github.com/ryo-akaiwa/gazou_kadai/blob/master/image05/LLENN.jpg?raw=true)
図1　原画像

この画像を

ORG=imread('Lenna.png'); % 原画像の入力  
ORG = rgb2gray(ORG); % カラー画像を白黒濃淡画像へ変換  
imagesc(ORG); colormap(gray); colorbar;

によって白黒濃淡画像に変換し、表示した結果を図2に示す。

![原画像](https://github.com/ryo-akaiwa/gazou_kadai/blob/master/image05/kadai5_1.png?raw=true)
図2　白黒濃淡画像

また、この画像を

H = imhist(ORG); %ヒストグラムのデータを列ベクトルEに格納  
myu_T = mean(H);  
max_val = 0;  
max_thres = 1;  
for i=1:255  
C1 = H(1:i); %ヒストグラムを2つのクラスに分ける  
C2 = H(i+1:256);  
n1 = sum(C1); %画素数の算出  
n2 = sum(C2);  
myu1 = mean(C1); %平均値の算出  
myu2 = mean(C2);  
sigma1 = var(C1); %分散の算出  
sigma2 = var(C2);  
sigma_w = (n1 *sigma1+n2*sigma2)/(n1+n2); %クラス内分散の算出

sigma_B = (n1 *(myu1-myu_T)^2+n2*(myu2-myu_T)^2)/(n1+n2); %クラス間分散の算出  
if max_val<sigma_B/sigma_w  
max_val = sigma_B/sigma_w;  
max_thres =i;  
end;  
end;

IMG = ORG > max_thres;  
imagesc(IMG); colormap(gray); colorbar;

によって画像を二値化した結果を図３に示す。

![原画像](https://github.com/ryo-akaiwa/gazou_kadai/blob/master/image05/kadai5_2.png?raw=true)
図3　２値化した画像

判別分析法は、ある閾値でそれより下の部分のクラスとそれ以上のクラスと分けたときにその２つ間の間分散とそれぞれのクラスの内分散の比が最も大きくなるときの閾値を求めるものである。
　その結果、最大の閾値max_thresの値は172であった。したがって今回は閾値が172となり、２値化されていることが分かった。
　また、図３と図２を比較すると、画像が判別できるように２値化出来ていることが分かった。
