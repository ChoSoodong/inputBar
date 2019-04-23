# inputBar
输入工具条,输入框和发送
```
-(void)setTextViewToolbar {
    self.inputToolbar = [[SDInputToolbar alloc] init];
    [self.inputToolbar updateWithConfig:^(SDInputToolbarConfigure *configure) {
        //这里的block是一个局部变量，不会造成循环引用，内部可以使用self
        NSLog(@"我不会被循环引用%@",self);
        configure.textViewMaxLine = 4;
        configure.font = [UIFont systemFontOfSize:10];
        configure.showMaskView = NO;
//        configure.cursorColor = [UIColor redColor];
//        configure.textColor = cl_RandomColor;
//        configure.backgroundColor = cl_RandomColor;
//        configure.topLineColor = cl_RandomColor;
//        configure.bottomLineColor = cl_RandomColor;
//        configure.edgeLineViewColor = cl_RandomColor;
//        configure.sendButtonBorderColor = cl_RandomColor;
//        configure.sendButtonTextColor = cl_RandomColor;
//        configure.placeholderTextColor = cl_RandomColor;
    }];
    __weak __typeof(self) weakSelf = self;
    [self.inputToolbar inputToolbarSendText:^(NSString *text) {
        __typeof(&*weakSelf) strongSelf = weakSelf;
        NSLog(@"%@",text);
        [strongSelf.btn setTitle:text forState:UIControlStateNormal];
        // 清空输入框文字
        [strongSelf.inputToolbar clearText];
    }];
}


```
