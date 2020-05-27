# Cài đặt git #  
 
## Với windows:  
Nếu bạn dùng Windows thì có thể tải file .exe cài đặt Git tại địa chỉ http://git-scm.com/download/win. Khi cài bạn có thể để nguyên tùy chọn mặc định mà không cần tùy chỉnh gì thêm nếu bạn chưa hiểu về nó.

Sau khi cài đặt Git vào Windows, bạn sẽ cần mở ứng dụng Git Bash lên để bắt đầu sử dụng các dòng lệnh của Git.

## Với Ubuntu:  
$ sudo apt-get install git  
## Với Mac:  
Bạn có thể sử dụng file installer tải tại địa chỉ http://git-scm.com/download/mac để cài đặt.  

**Thiết lập chứng thực cá nhân**  
Sau khi cài Git xong, việc đầu tiên bạn nên làm là khai báo tên và địa chỉ email vào trong file cấu hình của Git trên máy. Để làm điều này bạn sẽ cần sử dụng hai lệnh sau đây để thiết lập tên và email.

$ git config --global user.name "nobugnolife"  

$ git config --global user.email "nobugnolife@gmail.com"  

Sau khi thiết lập xong, bạn có thể kiểm tra thông tin chứng thực trên user của bạn bằng cách xem tập tin ~/.gitconfig (nhắc lại rằng dấu ~ nghĩa là thư mục gốc của user).  

$ cat ~/.gitconfig  

Hoặc bạn cũng có thể dùng lệnh git config –list để ghi danh sách các thiết lập hiện tại mà bạn đã làm.  

Như vậy là bạn đã xong bước ban đầu đó là cài đặt Git và thiết lập tên và email của mình vào Git để bắt đầu làm việc. Ở phần sau, mình sẽ hướng dẫn cách bạn tạo ra một local repository (kho chứa trên máy cá nhân) để xem Git hoạt động thế nào.  

## Cách tạo một repository  
**Repository** (kho chứa) nghĩa là nơi mà bạn sẽ lưu trữ mã nguồn và một người khác có thể sao chép (clone) lại mã nguồn đó nhằm làm việc. Repository có hai loại là Local Repository (Kho chứa trên máy cá nhân) và Remote Repository (Kho chứa trên một máy chủ từ xa).  

Trong bài này, mình sẽ hướng dẫn bạn cách tạo local repository và remote repository (sử dụng Github) và làm việc với nó.  

### Tạo local repository  ###  
Trước hết, để tạo một repository thì bạn cần truy cập vào thư mục của mã nguồn với lệnh cd, sau đó sử dụng lệnh git init để khởi tạo repository trong thư mục đó. Ở ví dụ này, mình sẽ tạo ra một thư mục mới để chứa code sau này và khởi tạo repository cho nó, mình sẽ dùng lệnh git init tên_folder để nó tự khởi tạo thư mục.

**$ git init git_example**

Ở đoạn trên, nó hiển thị dòng thông báo mình đã khởi tạo một kho Git trống tại đường dẫn như trên. Lưu ý rằng thư mục ẩn .git/ là nơi nó sẽ chứa các thiết lập về Git cũng như lưu lại toàn bộ thông tin về kho chứa, bạn không cần đụng chạm gì vào thư mục .git/ này.

Nếu kho chứa của bạn đã có sẵn mã nguồn thì bạn cần phải đưa các tập tin về trạng thái Tracked nhằm có thể làm việc được với Git. Để làm việc này, bạn sẽ cần sử dụng lệnh git add tên_file, có thể sử dụng dấu * để gom toàn bộ. Sau đó có thể sử dụng lệnh git status để xem danh sách các tập tin đã được tracked.  

**$ git add readme.txt**  
**$ git status**  

Và sau khi tập tin đã được đưa vào trạng thái tracked và nếu một tập tin đã tracked thì nó phải được đưa vào lại Staging Area (giải thích ở bài sau) cũng bằng lệnh git add thì bạn mới có thể tiến hành ủy thác (commit) nhằm lưu lại bản chụp các thay đổi. Lệnh commit sẽ có cấu trúc git commit -m “Lời nhắn”, lúc này tất cả các tập đang trong trạng thái tracked (file mới) hoặc một tập tin đã được tracked nhưng có một sự thay đổi mới thì sẽ được commit.

**$ git commit -m "First Commit"**  

Bây giờ thì bạn đã hoàn thành việc commit lần đầu tiên các tập tin mà bạn đã đưa vào kho, mình sẽ nói kỹ hơn về việc commit ở các bài sau. Tóm lại là tới đây bạn đã có một kho chứa mã nguồn Git trên máy của bạn.  

## Tạo repository trên Github và làm việc ##  
Trước tiên bạn cần đăng nhập vào Github, sau đó ấn vào dấu + trên menu và chọn New repository.  

Bạn sẽ cần đặt tên cho kho chứa của bạn. Bạn có thể chọn loại kho chứa là Public (ai cũng có thể clone) và Private (chỉ có những người được cấp quyền mới có thể clone).  

Khi tạo xong nó sẽ dẫn bạn tới trang hướng dẫn làm việc với kho chứa vừa tạo. Và kho chứa của bạn bây giờ sẽ có địa chỉ là https://github.com/$user-name/$repository, ví dụ https://github.com/thuank42/test.

Việc của bạn bây giờ là hãy clone cái kho chứa này về máy của mình bằng lệnh git clone địa_chỉ.  

**$ git clone https://github.com/thuank42/test**   
Bây giờ hãy truy cập vào thư mục working tree (thư mục vừa clone repository về) và thử tạo ra một file tên là **README.md**, sau đó dùng lệnh git add để đưa file này vào Staging Area.

**$ cd test**   
**$ echo "# Huong dan Git co ban" > README.md**  
**$ git add README.md**  
**$ git commit -m "First commit on Github"**  

Tuy nhiên sau khi commit xong, tập tin đã được commit sẽ vẫn không thể xuất hiện trong kho chứa trên Github mà bạn phải làm thêm một việc nữa đó là dùng lệnh git push để đẩy các tập tin đã được commit lên Github. Lưu ý rằng bạn sẽ cần nhập tài khoản và mật khẩu Github.

origin nghĩa là tên remote (xem ở bài sau) và master là tên branch, hai cái này mình sẽ giải thích kỹ hơn ở bài riêng của nó.

Trong bài tạo repository cho Git mình có nhắc qua về cụm từ Staging Area và một tính năng là commit (ủy thác), vậy hai cái này là gì thì mình sẽ giải thích kỹ hơn trong bài này để bạn biết cách sử dụng cho đúng.

## Staging Area là gì? ##  
**Staging Area** nghĩa là một khu vực mà nó sẽ được chuẩn bị cho quá trình commit. Trước hết, bạn cần phải hiểu rằng trong các hệ thống quản lý phiên bản (Version Control System) thì các dữ liệu sẽ được lưu trữ ở hai nơi, một là thư mục bạn đang làm việc trên máy tính (working tree, mình không nhắc lại nữa đâu) và một là kho chứa mã nguồn (repository) sau khi bạn đã thực hiện thay đổi (ví dụ như kho chứa trên Github).  

Nhưng với Git thì nó có thêm một lựa chọn nữa đó là có thêm một khu vực trung gian gọi là Staging Area và đây chính là một lợi thế lớn của Git. Staging Area nghĩa là khu vực sẽ lưu trữ những thay đổi của bạn trên tập tin để nó có thể được commit, vì muốn commit tập tin nào thì tập tin đó phải nằm trong Staging Area. Một tập tin khi nằm trong Staging Area sẽ có trạng thái là Stagged (xem thêm ở dưới).

![image](https://cddos.net/upload/images/9465124579.jpg)

Và để đưa một tập tin vào Staging Area thì bạn sẽ cần phải sử dụng lệnh git add tên_file mà mình đã có ví dụ ở phần trước.  

## Commit là gì và nó hoạt động ra sao? ##  
Hiểu đơn giản hơn, commit nghĩa là một hành động để Git lưu lại một bản chụp (snapshot) của các sự thay đổi trong thư mục làm việc, và các tập tin và thư mục được thay đổi đã phải nằm trong Staging Area. Mỗi lần commit nó sẽ được lưu lại lịch sử chỉnh sửa của mã nguồn kèm theo tên và địa chỉ email của người commit. Ngoài ra trong Git bạn cũng có thể khôi phục lại tập tin trong lịch sử commit của nó để chia cho một phân nhánh (branch) khác, đây là mấu chốt của việc bạn sẽ dễ dàng khôi phục lại các thay đổi trước đó mà mình có giới thiệu qua ở phần giới thiệu serie này.  

Và tất nhiên, lệnh commit trong Git sẽ là **git commit -m “Lời nhắn”** .  

Và nếu bạn muốn đưa tập tin lên repository thì bạn phải commit nó trước rồi sau đó lệnh **git push origin master** sẽ có nhiệm vụ đưa toàn bộ các tập tin đã được commit lên repository.

## Điều kiện gì để commit một tập tin? ##  
Nếu bạn muốn commit một tập tin đó, bạn sẽ cần phải đưa tập tin đó vào trạng thái tracked bằng lệnh git add tên_file. Trong git có hai loại trạng thái chính đó là Tracked và Untracked, cụ thể:  

Tracked – Là tập tin đã được đánh dấu theo dõi trong Git để bạn làm việc với nó. Và trạng thái Tracked nó sẽ có thêm các trạng thái phụ khác là Unmodified (chưa chỉnh sửa gì), Modified (đã chỉnh sửa) và Staged (đã sẵn sàng để commit). Untracked – Là tập tin còn lại mà bạn sẽ không muốn làm việc với nó trong Git.  

Nhưng bạn phải nên biết rằng nếu tập tin đó đã được Tracked nhưng đang rơi vào trạng thái (Modified) thì nó vẫn sẽ không thể commit được mà bạn phải đưa nó về Staged cũng bằng lệnh **git add**.  

## Bỏ qua Staging Are để commit ##  
Như mình có nói ở trên là một tập tin sau khi được thay đổi hay tạo mới thì nó phải được thêm vào Staging Area với lệnh git add. Tuy nhiên, bạn có thể đưa một tập tin đã được Tracked để commit mà không cần đưa nó vào Staging Area với tham số -a trong lệnh git commit. Ví dụ: **git commit -a -m “Skipped Staging Are to commit”**.

## Tìm hiểu thêm về trạng thái ##  

![image](https://cddos.net/upload/images/7459427859.jpg)

### Untracked ###  
Nếu bạn tạo ra hoặc thêm vào một tập tin mới vào trong thư mục làm việc của bạn thì nó sẽ ở trạng thái *Untracked*. Bây giờ mình thử tạo ra một tập tin mới tên là faq.html, sau đó dùng lệnh git status để xem trạng thái của Git trong thư mục làm việc.  

**$ touch faq.html**  
**$ git status**  

**Note:** Lệnh touch là tạo ra một tập tin rỗng.  

Bây giờ bạn sẽ thấy nó đã liệt kê ra tên tập tin đang ở trạng thái Untracked. Để đưa nó về Tracked bạn sẽ sử dụng lệnh git add và xem lại trạng thái của nó.  

Bây giờ bạn thấy, tập tin faq.html của mình đã được đưa về trạng thái Staged và nó có thể được commit. Tại sao? Vì bạn phải biết rằng nếu một tập tin ở trạng thái Untracked mà được đưa về Tracked thì nó sẽ nằm ở trạng thái Staged luôn, trừ khi bạn thay đổi nội dung tập tin này thì nó sẽ đưa về trạng thái Modified và nó không thể commit trừ khi bạn gõ lệnh git add cho nó.   

### Tracked ###  
Một khi một tập tin đã được đưa về **Tracked** thì nó sẽ có thể thay đổi giữa 3 trạng thái khác nhau là **Modified, Unmodified và Staged**.

Trước hết bây giờ mình đã có một tập tin mới đã được đưa về Staged với lệnh git add như ví dụ trên. Bây giờ mình tiến hành thay đổi nội dung của tập tin faq.html này và xem kết quả của lệnh **git status**.  

**$ git status**  

Bạn có thấy sự kỳ lạ ở tập tin faq.html không? Đó là nó được hiển thị ở hai trạng thái Staged (có thể commit) và Modified (không thể commit) hay còn gọi là Unstaged. Sở dĩ có sự kỳ lạ đó ở đây là bởi vì trước đó bạn đã tạo ra tập tin faq.html và đưa về Tracked thì nó cũng đã được đưa về Staged để có thể commit. Tuy nhiên sau đó bạn lại chỉnh sửa nội dung của nó nên nó đã có một phiên bản khác nằm ở trạng thái Modified (không thể commit). Nếu bây giờ bạn gõ lệnh git commit để ủy thác nó thì bản chụp của tập tin faq.html ở lần cuối cùng bạn gõ lệnh git add sẽ được commit lên chứ nó không chứa các nội dung mà bạn vừa thêm vào. Và để nó có thể commit tập tin faq.html đã được chỉnh sửa thì bạn phải gõ lại lệnh git add faq.html lần nữa.

### Chuyển tập tin từ Untracked về Tracked ###  
Trong Git, bạn có thể đưa một tập tin từ Tracked về Untracked với lệnh rm tên_file. Lệnh rm sẽ giúp bạn đưa tập tin về trạng thái Untracked nhưng không xóa hẳn trong ổ cứng.  

**$ rm faq.html** 
**$ git status**  

Còn nếu bạn muốn xóa nó luôn thì dùng lệnh **git rm -f tên_file** và nhớ cẩn thận khi dùng lệnh này.

## Sơ lược remote respository và origin ##  

Quay trở lại bài tạo repository, mình có hướng dẫn bạn cách tạo một repository trên dịch vụ Github và Clone nó về máy. Như vậy, cái Github là một máy chủ repository từ xa nên mình sẽ gọi nó là Remote Repository, nghĩa là repository này không nằm trên máy tính của bạn.

Và ở phần đó, bạn có thấy mình kêu các bạn gửi dữ liệu lên repository bằng cách dùng lệnh git push origin master sau khi commit không? Cái master là tên branch mà mình sẽ không nói ở bài này, nhưng cái origin trong đoạn đó chính là tên remote repository. Mặc định khi clone một repository thì nó tự đặt tên là origin.

Để kiểm tra tên remote, bạn có thể gõ lệnh **git remote -v**.

Trong đó bạn có thể thấy cái repository mình đã clone đều được đặt tên là origin, và mỗi repository bạn có hai đều có hai hành động là fetch (lấy dữ liệu về từ server) và push (gửi dữ liệu lên server).

Nhìn lại đoạn lệnh git push origin master ở trên, điều đó có nghĩa là bạn gửi tất cả các thay đổi trên mã nguồn ở máy bạn lên remote tên là origin với branch master.

### Đổi tên remote ###  

Nếu bạn không thích tên origin thì có thể đổi tên nó lại nó bằng tên khác cho dễ quản lý nếu như bạn có nhiều remote trong một dự án với lệnh **git remote rename tên_cũ tên_mới**. Ví dụ mình cần đổi từ origin sang binh thì sẽ đổi như sau:  

**$ git remote rename origin thuan**  
**$ git remote -v**  

Bây giờ khi commit hay push bạn có thể gõ git push thach master để gửi mã nguồn lên remote repository này.

### Thêm một remote ###  

Trường hợp bạn cần thêm một cái remote để lấy dữ liệu khi cần thì có thể sử dụng lệnh **git remote add tên_remote URL**. Ví dụ mình cần remote một repository và đặt tên nó là inuit thì sẽ viết như sau:

**$ git remote add snippet https://github.com/thuank42/rsnippet**  
**$ git remote -v**  

Sau đó nếu bạn muốn lấy dữ liệu từ cái snippet kia về thì chỉ cần sử dụng lệnh **git fetch snippet**  

Lưu ý là lệnh git fetch nó chỉ lấy về và lưu vào database của Git trên máy chứ không được gộp vào repository của bạn. Để gộp vào bạn có thể gõ thêm lệnh git merge snippet, trong đó snippet là tên remote.  

Còn nếu bạn muốn nó lấy về trực tiếp mà không cần gộp thì sử dụng lệnh git pull tên_remote, tuy nhiên mình khuyến khích bạn nên gộp vào branch khi cần và nhớ cẩn thận trong việc gộp, tốt nhất nên tạo thư mục mới trong thư mục làm việc của bạn rồi vào đó mà lấy về.

## Sự khác nhau giữa clone, fetch và pull ##  

Có thể bây giờ bạn đã biết được 3 lệnh để lấy dữ liệu về từ repository đó là *git clone, git fetch và git pull*. Nhưng cả ba loại đều là lấy dữ liệu, thế sự khác nhau của nó là gì?

### git clone ###  
Lệnh này sẽ sao chép toàn bộ dữ liệu trên repository và sao chép luôn các thiết lập về repository, tức là nó sẽ tự động tạo một master branch trên máy tính của bạn. Lệnh này chỉ nên sử dụng khi bạn cần tạo mới một Git mới trên máy tính với toàn bộ dữ liệu và thiết lập của một remote repository.

### git pull ###  
Lệnh này sẽ tự động lấy toàn bộ dữ liệu từ remote repository và gộp vào cái branch hiện tại bạn đang làm việc.

### git fetch ###
Lệnh này sẽ lấy toàn bộ dữ liệu từ remote repository nhưng sẽ cho phép bạn gộp thủ công vào một branch nào đó trên thư mục Git ở máy tính.

Tạm thời bạn nên hiểu thế, ở bài branch bạn sẽ hiểu sâu hơn.

## Các loại giao thức của Remote Repository ##  

Chúng ta không chỉ kết nối với một remote repository qua giao thức HTTP hay HTTPS mà còn có thể chọn nhiều giao thức khác, dưới đây là một vài giao thức remote repository.

### Local Repository ###  
Giao thức này nghĩa là bạn kết nối tới một repository nào đó trên chính máy tính của bạn và URL của giao thức sẽ có dạng /path/repository/.

### HTTP Repository ###  
Giao thức thông dụng nhất cũng như dễ hiểu nhất, thường được sử dụng nếu bạn dùng các dịch vụ remote repository như Github hay Assembla, nó sẽ bao gồm định dạng http://domain.com/repository.git hoặc https://domain.com/repository.git.

### SSH Repository ###
Giao thức này thường được dùng trên các nhu cầu tạo một server repository riêng và kết nối thông qua giao thức SSH. Đường dẫn của giao thức này sẽ có dạng là user@server:/path/repository.git. Ở phần cuối serie mình sẽ hướng dẫn bạn cách tạo một repository server riêng và nó là lựa chọn rất tốt nếu bạn làm việc nhóm mà không cần phụ thuộc vào các dịch vụ như Github hay Assembla.
