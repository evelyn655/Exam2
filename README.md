##[ Part I ]

在 screen 輸入指令 /Gesture_UI/run，呼叫RPC function: Gesture_UI
Gesture_UI 會 call thread function: gesture_ui，在 gesture_ui 中會進行手勢辨識，擷取特色。
會將辨識出的手勢 publish 到 python 端，同時 python 端有訂閱 topic1，所以會接收到訊息。
python 端接收到 10 次訊息後，會在 screen 寫入 /Leave_Mode/run，該 RPC function 使 mbed 跳出 Angle_Detection 模式。

##[ Part II ]
在 screen 輸入指令 /PLOT/run，呼叫RPC function: PLOT
在這個 function 裡面，會印出辨識到 10 次的手勢名稱及其 feature (該手勢第一個測到的角度是否大於 15度)

並且 uLCD 會顯示相關訊息


