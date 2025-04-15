ComfyUI-api 功能介绍

功能列表
中文功能介绍
1. 查询当前任务数量
功能描述：可查询 ComfyUI 当前的任务数量，并将结果显示在页面上。
实现方式：向 ComfyUI 的 /prompt 接口发送 GET 请求来获取任务队列信息。
2. 发起新任务
功能描述：从指定的 JSON 文件读取工作流数据，对其中特定内容进行修改，如变更字符串和随机化种子，之后向 ComfyUI 的 /prompt 接口发起 POST 请求以发起新任务。可设置 number 和 front 参数来控制任务执行顺序和优先级。
实现方式：读取指定 JSON 文件的数据，修改内容后向 /prompt 接口发送 POST 请求。
3. 获取历史任务记录
功能描述：获取 ComfyUI 的历史任务记录，涵盖所有任务和单个任务的记录。
实现方式：通过向 /history 和 /history/{prompt_id} 接口发送 GET 请求来实现。
4. 获取模型配置信息
功能描述：获取 ComfyUI 中模型（例如 LoRA、Checkpoints 等）的配置信息。
实现方式：向 /models/{文件夹名称} 接口发送 GET 请求获取信息。
5. 获取组件信息
功能描述：获取 ComfyUI 各组件的详细信息，既可以根据组件名称进行查询，也能获取所有组件信息。
实现方式：向 /object_info/{组件名称} 接口发送 GET 请求，若不指定组件名称则返回所有组件信息。
6. 上传图片或遮罩
功能描述：支持上传图片或遮罩到 ComfyUI，上传时可设置相关参数罩到 ComfyUI，上传时可设置相关参数。
实现方式：创建 FormData 对象，将图片或遮罩添加到其中，然后向 /upload/image 或 /upload/mask 接口发送 POST 请求。
7. 取消队列和当前任务
功能描述：提供取消 ComfyUI 任务队列和当前正在执行任务的功能。
实现方式：向 /queue 接口发送包含 delete 字段的 POST 请求取消队列，向 /interrupt 接口发送 GET 请求取消当前任务。
8. 获取当前执行中的和队列中的任务
功能描述：获取 ComfyUI 当前正在执行和队列中的任务信息，对返回数据进行整理，输出正在运行的任务、待处理的任务以及客户端 ID。
实现方式：向 /queue 接口发送 GET 请求实现。
9. 图片在线预览或获取地址
功能描述：提供输入图片和输出图片的在线预览功能或获取图片地址。
实现方式：将 /view?type={input/output}&filename={文件名} 拼接到 ComfyUI 地址来实现。
10. 实时的 websocket 连接
功能描述：建立与 ComfyUI 的 WebSocket 连接，实时接收任务执行状态、队列信息、节点进度等消息，并进行相应处理和输出。
实现方式：建立 WebSocket 连接并处理接收到的消息。
11. 实时监控（实时出图）
功能描述：通过 WebSocket 连接实时监控任务执行过程，当接收到 executed 类型的消息时，可获取输出图片名称，结合图片在线预览功能实现实时出图的监控。
实现方式：通过 WebSocket 监控任务执行，结合图片预览功能实现。
12. 发起任务的插队
功能描述：在发起新任务时，通过设置 front 参数为较大值，保证该任务具有较高的执行优先级，实现插队执行。
实现方式：发起新任务时设置 front 参数。
English Function Introduction
1. Query the current number of tasks
Function Description: Query the current number of tasks in ComfyUI and display the result on the page.
Implementation Method: Send a GET request to the /prompt interface of ComfyUI to obtain task queue information.
2. Initiate a new task
Function Description: Read the workflow data from a specified JSON file, modify specific content such as changing strings and randomizing seeds, and then send a POST request to the /prompt interface of ComfyUI to initiate a new task. You can set the number and front parameters to control the task execution order and priority.
Implementation Method: Read data from the specified JSON file, modify the content, and then send a POST request to the /prompt interface.
3. Get historical task records
Function Description: Retrieve historical task records in ComfyUI, including records of all tasks and individual tasks.
Implementation Method: Achieve this by sending GET requests to the /history and /history/{prompt_id} interfaces.
4. Get model configuration information
Function Description: Obtain configuration information of models (such as LoRA, Checkpoints, etc.) in ComfyUI.
Implementation Method: Send a GET request to the /models/{folder_name} interface to get the information.
5. Get component information
Function Description: Retrieve detailed information of each component in ComfyUI. You can query by component name or get information of all components.
Implementation Method: Send a GET request to the /object_info/{component_name} interface. If no component name is specified, information of all components will be returned.
6. Upload images or masks
Function Description: Support uploading images or masks to ComfyUI, and relevant parameters can be set during uploading.
Implementation Method: Create a FormData object, add the image or mask to it, and then send a POST request to the /upload/image or /upload/mask interface.
7. Cancel the queue and the current task
Function Description: Provide the function to cancel the task queue and the currently executing task in ComfyUI.
Implementation Method: Cancel the queue by sending a POST request containing the delete field to the /queue interface, and cancel the current task by sending a GET request to the /interrupt interface.
8. Get currently executing and queued tasks
Function Description: Obtain information about the tasks currently being executed and in the queue in ComfyUI. Organize the returned data and output the running tasks, pending tasks, and client IDs.
Implementation Method: Achieve this by sending a GET request to the /queue interface.
9. Online image preview or get image address
Function Description: Provide the function of online preview or getting the address of input and output images.
Implementation Method: Achieve this by appending /view?type={input/output}&filename={file_name} to the ComfyUI address.
10. Real - time WebSocket connection
Function Description: Establish a WebSocket connection with ComfyUI to receive real - time messages such as task execution status, queue information, and node progress, and perform corresponding processing and output.
Implementation Method: Establish a WebSocket connection and process the received messages.
11. Real - time monitoring (real - time image output)
Function Description: Monitor the task execution process in real - time through the WebSocket connection. When a message of type executed is received, the output image name can be obtained, and real - time image output monitoring can be realized in combination with the online image preview function.
Implementation Method: Monitor task execution through WebSocket and combine with the image preview function.
12. Task queuing up
Function Description: When initiating a new task, set the front parameter to a larger value to ensure that the task has a higher execution priority and achieve queuing up for execution.
Implementation Method: Set the front parameter when initiating a new task.
