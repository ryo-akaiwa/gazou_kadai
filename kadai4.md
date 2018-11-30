# 課題4　レポート

　画像｢LLENN｣を原画像として用いる。この画像は縦841画素、横841画素である。

この原画像を図1に示す。

![原画像](https://github.com/ryo-akaiwa/gazou_kadai/blob/master/image04/LLENN.jpg?raw=true)  
図1　原画像

この画像を

ORG=imread('LLENN.jpg'); % 原画像の入力  
ORG=rgb2gray(ORG); % カラー画像を白黒濃淡画像へ変換  
imagesc(ORG); colormap(gray); colorbar;

によって読み取り、白黒濃淡画像に変換して表示した結果を図2に示す。

![原画像](https://github.com/ryo-akaiwa/gazou_kadai/blob/master/image04/kadai4_1.png?raw=true)
図2　白黒濃淡画像

また、この画像を

imhist(ORG); % ヒストグラムの表示

によって濃度値のヒストグラムを表示した結果を図3に示す。

![原画像](https://github.com/ryo-akaiwa/gazou_kadai/blob/master/image04/kadai4_2.png?raw=true)
図3　ヒストグラム

この結果からこの画像には約50～80、160、240の濃度値が多く含まれていることが分かる。  
このことから、画像の特定の濃度に対してなにか処理したいときは、ヒストグラムによって濃度を分析することが有効であると思われる。
