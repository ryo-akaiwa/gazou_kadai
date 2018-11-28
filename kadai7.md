# 課題7レポート

画像｢LLENN｣を原画像として用いる。この画像は縦841画素、横841画素である。

この画像を

ORG=imread('kirimichan.png'); % 原画像の入力  
ORG= rgb2gray(ORG); % カラー画像を白黒濃淡画像へ変換  
imagesc(ORG); colormap(gray); colorbar; % 画像の表示

によって読み込み、白黒濃淡画像へ変形して表示した結果を図1に示す。

![原画像](https://github.com/ryo-akaiwa/gazou_kadai/blob/master/image07/kadai7_1.png?raw=true)
図1　白黒濃淡画像

また、図1の画像の濃度ヒストグラムは図2のようなる。

![原画像](https://github.com/ryo-akaiwa/gazou_kadai/blob/master/image07/kadai7_2.png?raw=true)
図2　図1の濃度ヒストグラム

次に、図1の画像の

ORG = double(ORG);  
mn = min(ORG(:)); % 濃度値の最小値を算出  
mx = max(ORG(:)); % 濃度値の最大値を算出  
ORG = (ORG-mn)/(mx-mn)*255;  
imagesc(ORG); colormap(gray); colorbar; % 画像の表示  

によって、ダイナミックレンジを0から255にしたものを図3に示す。

![原画像](https://github.com/ryo-akaiwa/gazou_kadai/blob/master/image07/kadai7_3.png?raw=true)
図3　ダイナミックレンジ拡大後の画像

また、図3の濃度ヒストグラムは図4のようになる。

![原画像](https://github.com/ryo-akaiwa/gazou_kadai/blob/master/image07/kadai7_4.png?raw=true)
図4　図3の濃度ヒストグラム

　この結果、図2と図4のヒストグラムを比べると、図2の濃度値が小さいところにはなかった濃度が図4では表れていることが分かる。  
　また、図4では成分が全くない濃度値がいくつか表れていることが分かる。これは、濃度値の計算をする前に画像を小数型であるdouble型にしているが、その後

ORG = uint8(ORG);

によって8ビットの符号なしの整数にしている。このときのORGの濃度値をdouble型を図5、unit8を図6に示す。

![原画像](https://github.com/ryo-akaiwa/gazou_kadai/blob/master/image07/kadai7_5.png?raw=true)
図5　double型のORGの濃度値

![原画像](https://github.com/ryo-akaiwa/gazou_kadai/blob/master/image07/kadai7_6.png?raw=true)
図6　unit8のORGの濃度値

このように、小数で表されているものが整数型にされているため、その結果、成分がない濃度値が表れてくると考えられる。
