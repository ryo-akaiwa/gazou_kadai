# 課題10レポート

　画像｢LLENN｣を原画像として用いる。この画像は縦841画素、横841画素である。

この原画像を図1に示す。

![原画像](https://github.com/ryo-akaiwa/gazou_kadai/blob/master/image07/LLENN.jpg?raw=true)  
図1　原画像

この画像を

ORG = imread('Lenna.jpg'); % 原画像の入力  
ORG = rgb2gray(ORG); %カラーからグレイへの変換  
imagesc(ORG); colormap('gray'); colorbar;% 画像表示

によって画像を読み込み、白黒濃淡画像へ変形して表示した結果を図2に示す。

![原画像](https://github.com/ryo-akaiwa/gazou_kadai/blob/master/image10/kadai10_1.jpg?raw=true)
図2　白黒濃淡画像

図2の画像を

IMG = edge(ORG,'prewitt'); % エッジ抽出（プレウィット法）  
imagesc(IMG); colormap('gray'); colorbar;% 画像表示

によってプレウィット法でエッジ抽出した結果を図3に示す。

![原画像](https://github.com/ryo-akaiwa/gazou_kadai/blob/master/image10/kadai10_2.jpg?raw=true)
図3　プレウィット法によるエッジ抽出

同様に

IMG = edge(ORG,'sobel'); % エッジ抽出（ソベル法）  
imagesc(IMG); colormap('gray'); colorbar;% 画像表示

によってソベル法でエッジ抽出した結果を図4に示す。

![原画像](https://github.com/ryo-akaiwa/gazou_kadai/blob/master/image10/kadai10_3.jpg?raw=true)
図4　ソベル法によるエッジ抽出

また、同じように

IMG = edge(ORG,'canny'); % エッジ抽出（キャニー法）  
imagesc(IMG); colormap('gray'); colorbar;% 画像表示

によってキャニー法でエッジ抽出した結果を図5に示す。

![原画像](https://github.com/ryo-akaiwa/gazou_kadai/blob/master/image10/kadai10_4.jpg?raw=true)
図5　キャニー法によるエッジ抽出

　プレウィット法では、注目しているものの輪郭を抽出していることが分かる。また、ソベル法は、プレウィット法では抽出していなかった細かい所の輪郭まで抽出していることが分かる。しかし、ソベル法はノイズの影響も大きくなってしまうことが分かる。したがって、ノイズが少ない方が良いとき、またはエッジの検出感度が高い方が良いのかで使い分けする必要があると考えられる。  
　キャニー法は図5を見て分かるようにとても感度の良いエッジ検出であると思われる。この方法は一旦画像を平滑化してからエッジ抽出を行うため、ノイズも少なくなること理解出来た。

これらより、注目しているものを大まかに抽出するにはプレウィット法、ソベル法は使うことが出来ると思う。しかし、キャニー法は綺麗に抽出されており、正確性を求められるところなどで様々な応用が利くものであると考えられる。
