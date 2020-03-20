# Swift UI
## Basic
- SwiftUI/Combineを使いMVVMで実装するときは、Viewに `@ObservedObject` なViewModelを定義して使うことが多い。ViewModelのGETプロパティに変更が加えられた時に、イベントが流れてくるので、それをbindすることでUIを更新できる。

```
struct SampleView: View {
    @ObservedObject private var viewModel: WhetherViewModel
    
    var body: some View {
        VStack {
            HStack {
                Text("今日の天気：")
                Text($viewModel.whetherOfToday)
            }
        }
    }


    // QUESTION: initializerはいらないのかな？？viewModelはどこからinjectするんだろう。
    // init(viewModel: WhetherViewModel) {
    //     self.viewModel = viewModel
    // }
}

struct WhetherViewModel {
    var whetherOfToday: String {
        return "晴れです"
    }
}

```


- 似たようなものに `@EnvironmentObject` があるが、複数の画面間で値の共有をしたい場合に使う（Session情報とかかなあ。この辺はあまり詳しくない。調べる必要ありそう。）



# Combine



### Special Thanks to
- [SwiftUI + CombineでMVVM](https://tech.88oct.co.jp/entry/2019/10/23/095058)
- [MVVM with Combine Tutorial for iOS / raywenderlich.com](https://www.raywenderlich.com/4161005-mvvm-with-combine-tutorial-for-ios)
- [MVVM with Combine Tutorial for iOS （日本語略版）](https://qiita.com/you_matz/items/a3d640be2a8feaf698bd)
