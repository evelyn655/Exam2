[ Part I ]
在 screen 輸入指令 /Gesture_UI/run，呼叫RPC function: Gesture_UI
Gesture_UI 會 call thread function: gesture_ui，在 gesture_ui 中會進行手勢辨識，並依據辨識出的不同手勢，進行角度選擇。
當使用者確定（按下 button）所選擇的角度後，mbed 會 publish 該數值至 topic1 "Angle selection"，同時 python 端有訂閱 topic1，所以會接收到訊息。
python 端接收到訊息後，會在 screen 寫入 /Leave_Mode/run，該 RPC function 使 mbed 跳出 Gesture_UI 模式。
[ Part II ]
在 screen 輸入指令 /Angle_Detection/run，呼叫RPC function: Angle_Detection
Angle_Detection 會 call thread function: angle_detection，在 angle_detection 中會計算目前 mbed 的傾角。
當 mbed 傾斜的角度超過 [ Part I ] 中所選擇的角度，mbed 會 publish 訊息至 topic2 "Angle detection"，同時 python 端有訂閱 topic2，所以會接收到訊息。
python 端接收到 10 次訊息後，會在 screen 寫入 /Leave_Mode/run，該 RPC function 使 mbed 跳出 Angle_Detection 模式。
