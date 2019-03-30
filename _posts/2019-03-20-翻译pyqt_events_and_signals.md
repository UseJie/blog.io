## PyQt5 的 事件和信号(Events and signals)

在Pyqt5的这一部分程序辅助中，我们将会探索事件和信号在应用中的作用。

## 事件（Events）

GUI应用都是事件驱动的。事件主要由应用的用户触发。但是他们也可以由其他的方法触发，例如网络连接、窗口管理或者计时器。当我们调用应用的exec_()函数的时候，应用会进去主循环。主循环捕捉事件然后发送它们给对象。

在事件模型中，有三个主要成分：
1. 事件源（event source）
2. 事件对象（event object）
3. 事件目标（event target）

对象状态的改变是事件源。它产生事件。在事件源中事件对象（event）包含状态的改变。事件的目标是一个想去被公布（notified）的对象。事件源对象委托处理（handing）一个事件的任务给一个事件目标。

PyQt5有独一无二的signal和slot机制处理事件。Signals和slots都被用来两个对象之间的通信。当特定的事件发生时，一个信号（signal）会被发射出去。槽（slot）可以被Python调用。槽（slot）在它的连接的信号被发射时会被调用。

## 信号和槽（Signals and slots）

这是一个简单的PyQt5的signals和slots例子。

‘’‘
#!/usr/bin/python3
# -*- coding: utf-8 -*-

"""
ZetCode PyQt5 tutorial 

In this example, we connect a signal
of a QSlider to a slot of a QLCDNumber. 

Author: Jan Bodnar
Website: zetcode.com 
Last edited: January 2017

Translation: Ajoy
Last Translated: 2019-3-22

"""

import sys
from PyQt5.QtCore import Qt
from PyQt5.QtWidgets import (QWidget, QLCDNumber, QSlider, 
    QVBoxLayout, QApplication)


class Example(QWidget):
    
    def __init__(self):
        super().__init__()
        
        self.initUI()
        
        
    def initUI(self):
        
        lcd = QLCDNumber(self)
        sld = QSlider(Qt.Horizontal, self)

        vbox = QVBoxLayout()
        vbox.addWidget(lcd)
        vbox.addWidget(sld)

        self.setLayout(vbox)
        sld.valueChanged.connect(lcd.display)
        
        self.setGeometry(300, 300, 250, 150)
        self.setWindowTitle('Signal and slot')
        self.show()
        

if __name__ == '__main__':
    
    app = QApplication(sys.argv)
    ex = Example()
    sys.exit(app.exec_())
’‘’

在我们的例子中，我们现实了一个QtGui.QLCDNumber和一个QtGui.QSlider。通过拖拉滑块按钮来改变lcd的数字。

'''
sld.valueChanged.connect(lcd.display)
'''

在这里我们将滑条的数值改变信号连接到lcd数字的显示槽中。

发送方（sender）是一个发送信号的对象。接受者（receiver）是一个接受信号的对象。槽（slot）是一个对信号作出反应的方法。
