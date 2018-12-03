# 課題9レポート

　画像｢LLENN｣を原画像として用いる。この画像は縦841画素、横841画素である。

この原画像を図1に示す。

![原画像](https://github.com/ryo-akaiwa/gazou_kadai/blob/master/image07/LLENN.jpg?raw=true)  
図1　原画像

この画像を

ORG=imread('LLENN.jpg'); % 原画像の入力  
ORG= rgb2gray(ORG); % カラー画像を白黒濃淡画像へ変換  
imagesc(ORG); colormap(gray); colorbar; % 画像の表示

によって読み込み、白黒濃淡画像へ変形して表示した結果を図2に示す。

![原画像](https://github.com/ryo-akaiwa/gazou_kadai/blob/master/image09/kadai9_1.jpg?raw=true)
図2　白黒濃淡画像

この画像に

ORG = imnoise(ORG,'salt & pepper',0.02); % ノイズ添付

とし、ノイズを添付した画像を図3に示す。

![原画像](https://github.com/ryo-akaiwa/gazou_kadai/blob/master/image09/kadai9_2.jpg?raw=true)
図3　ノイズを添付した画像

この図3の画像において

IMG = filter2(fspecial('average',3),ORG); % 平滑化フィルタで雑音除去

で平滑化フィルタで雑音を除去したものを図4に示す。

![原画像](https://github.com/ryo-akaiwa/gazou_kadai/blob/master/image09/kadai9_3.jpg?raw=true)
図4　平滑化フィルタ適用

また、図3の画像において

IMG = medfilt2(ORG,[3 3]); % メディアンフィルタで雑音除去

でメディアンフィルタで雑音を除去したものを図5に示す。

![原画像](https://github.com/ryo-akaiwa/gazou_kadai/blob/master/image09/kadai9_4.jpg?raw=true)
図5　メディアンフィルタ適用

また、

f=[0,-1,0;-1,5,-1;0,-1,0]; % フィルタの設計  
IMG = filter2(f,IMG,'same'); % フィルタの適用

とフィルタを設定し、このフィルタを図5の画像に適用したものを図6に示す。

![原画像](https://github.com/ryo-akaiwa/gazou_kadai/blob/master/image09/kadai9_5.jpg?raw=true)
図6　設計したフィルタを適用

平滑化フィルタは着目画素の周囲戸の平均値を取るものである。図4のように平衡化フィルタを適用したものは、にじんでいて、ぼやけて見える。また、ノイズが残ったままになっていることが分かった。  
メディアンフィルタは平滑化とは違い、着目画素の周囲との中央値を取るものである。図5のようにメディアンフィルタを適用したものは、エッジがぼやけることもなくきれいにノイズが消去できていることが分かった。

また、今回最後に設計したフィルタは鮮鋭化と呼ばれるもので、これを適用すると、図6のように輪郭部が強調されていることが分かった。
