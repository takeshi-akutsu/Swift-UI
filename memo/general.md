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