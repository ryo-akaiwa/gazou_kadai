# 課題7レポート

画像｢LLENN｣を原画像として用いる。この画像は縦841画素、横841画素である。

この原画像を図1に示す。

![原画像](https://github.com/ryo-akaiwa/gazou_kadai/blob/master/image07/LLENN.jpg?raw=true)
図1　原画像

この画像を

ORG=imread('LLENN.jpg'); % 原画像の入力  
ORG= rgb2gray(ORG); % カラー画像を白黒濃淡画像へ変換  
imagesc(ORG); colormap(gray); colorbar; % 画像の表示

によって読み込み、白黒濃淡画像へ変形して表示した結果を図2に示す。

![原画像](https://github.com/ryo-akaiwa/gazou_kadai/blob/master/image07/kadai7_1.png?raw=true)
図2　白黒濃淡画像

また、図2の画像の濃度ヒストグラムは図3のようなる。

![原画像](https://github.com/ryo-akaiwa/gazou_kadai/blob/master/image07/kadai7_2.png?raw=true)
図3　図1の濃度ヒストグラム

次に、図2の画像の

ORG = double(ORG);  
mn = min(ORG(:)); % 濃度値の最小値を算出  
mx = max(ORG(:)); % 濃度値の最大値を算出  
ORG = (ORG-mn)/(mx-mn)*255;  
imagesc(ORG); colormap(gray); colorbar; % 画像の表示  

によって、ダイナミックレンジを0から255にしたものを図4に示す。

![原画像](https://github.com/ryo-akaiwa/gazou_kadai/blob/master/image07/kadai7_3.png?raw=true)
図4　ダイナミックレンジ拡大後の画像

また、図4の濃度ヒストグラムは図5のようになる。

![原画像](https://github.com/ryo-akaiwa/gazou_kadai/blob/master/image07/kadai7_4.png?raw=true)
図5　図3の濃度ヒストグラム

　この結果、図3と図5のヒストグラムを比べると、図3の濃度値が小さいところにはなかった濃度が図5では表れていることが分かる。  
　また、図5では成分が全くない濃度値がいくつか表れていることが分かる。これは、濃度値の計算をする前に画像を小数型であるdouble型にしているが、その後

ORG = uint8(ORG);

によって8ビットの符号なしの整数にしている。このときのORGの濃度値をdouble型を図6、unit8を図7に示す。

![原画像](https://github.com/ryo-akaiwa/gazou_kadai/blob/master/image07/kadai7_5.png?raw=true)
図6　double型のORGの濃度値

![原画像](https://github.com/ryo-akaiwa/gazou_kadai/blob/master/image07/kadai7_6.png?raw=true)
図7　unit8のORGの濃度値

このように、小数で表されているものが整数型にされているため、その結果、成分がない濃度値が表れてくると考えられる。
