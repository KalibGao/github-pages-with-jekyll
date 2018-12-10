# Xamarin 常见问题

###  `StaticResource` 与 `DynamicResource` 的区别

- `StaticResource` 在`xaml`代码加载前,只运行一次, 所有动态`resource dictionary`的变更,会被忽略掉
- `DynamicResource`在`runtime`中任何需要加载的时候,都会动态加载. 例如数据绑定(会在数据加载完成后,动态应用`template` , `style`)



### `if is null` 延迟生成便捷写法

```chsarp

private string myValue;

public String MyValue => myValue ?? (myValue = "a value");

```


### `BindingContext`


```xml



```


### Command




### App Icon


### `Resources` 目录下, `drawable-*` 和 `mipmap-*` 选择规则

| 标识 | Level | 密度 | 比例  | Screen Size | 图标尺寸 | Action Bar | Notify Size
| :---: | :---: | --- | :---: | --- | --- | --- | ---
| ldpi  | 低 | ~120 dp | 0.75 | 426 * 320 | 36 * 36 | 24 * 24 | 18 * 18 
| mdpi | 中 | ~160 dp | 1.0 (基线) | 470 * 320 | 48 * 48 | 32 * 32 | 24 * 24
| hdpi | 高 | ~240 dp | 1.5 | 640 * 480 | 72 * 72 | 48 * 48 | 36 *36 
| xhdpi | 超高 | ~320 dp | 2.0 | 960 * 720 | 96 * 96 | 64 * 64 | 48 * 48
| xxhdpi | 超超高 | ~ 480 dp | 3.0 | 1280 * 960 | 144 * 144 | 96 * 96 | 72 * 72
| xxxhdpi | 超超超高 | ~ 640 dp | 4.0 | 1920 * 1440 | 192 * 192 | 128 * 128 | 96 * 96
 
### 隐藏`Navigation Header`

```csharp
public App()
{
    InitializeComponent();
    
    var mainPage = new MainPage();
    var navigation = new NavigationPage(mainPage);
    NavigationPage.SetHasNavigationBar(mainPage, false);

    MainPage = navigation;
}
```

### Android Tabbed Page 底部显示
C# Code: 
```csharp
using Xamarin.Forms.Xaml;
using Xamarin.Forms.PlatformConfiguration.AndroidSpecific;

namespace AName.Views
{
    [XamlCompilation(XamlCompilationOptions.Compile)]
    public partial class MainPage : Xamarin.Forms.TabbedPage
    { 
        public MainPage()
        {
            InitializeComponent();

            On<Xamarin.Forms.PlatformConfiguration.Android>().SetToolbarPlacement(ToolbarPlacement.Bottom);
        }

    }
}
```
