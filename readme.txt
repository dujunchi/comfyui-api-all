
查询当前任务数量：可以查询 ComfyUI 当前的任务数量，并将结果显示在页面上。通过向 ComfyUI 的/prompt接口发送 GET 请求获取任务队列信息。
发起新任务：从指定的 JSON 文件中读取工作流数据，对其中的特定内容进行修改，如变更字符串和随机化种子，然后向 ComfyUI 的/prompt接口发起 POST 请求，发起新的任务。可设置number和front参数控制任务执行顺序和优先级。
获取历史任务记录：获取 ComfyUI 的历史任务记录，包括所有任务和单个任务的记录。通过向/history和/history/{prompt_id}接口发送 GET 请求实现。
获取模型配置信息：获取 ComfyUI 中模型（如 LoRA、Checkpoints 等）的配置信息。通过向/models/{文件夹名称}接口发送 GET 请求获取。
获取组件信息：获取 ComfyUI 各组件的详细信息，可根据组件名称进行查询，也可获取所有组件信息。通过向/object_info/{组件名称}接口发送 GET 请求，若不指定组件名称则返回所有组件信息。
上传图片或遮罩：支持上传图片或遮罩到 ComfyUI，上传时可设置相关参数。通过创建 FormData 对象，将图片或遮罩添加到其中，然后向/upload/image或/upload/mask接口发送 POST 请求。
取消队列和当前任务：提供取消 ComfyUI 任务队列和当前正在执行任务的功能。通过向/queue接口发送包含delete字段的 POST 请求取消队列，向/interrupt接口发送 GET 请求取消当前任务。
获取当前执行中的和队列中的任务：获取 ComfyUI 当前正在执行和队列中的任务信息，对返回数据进行整理，输出正在运行的任务、待处理的任务以及客户端 ID。通过向/queue接口发送 GET 请求实现。
图片在线预览或获取地址：提供输入图片和输出图片的在线预览功能或获取图片地址。通过拼接/view?type={input/output}&filename={文件名}到 ComfyUI 地址实现。
实时的 websocket 连接：建立与 ComfyUI 的 WebSocket 连接，实时接收任务执行状态、队列信息、节点进度等消息，并进行相应处理和输出。
实时监控（实时出图）：通过 WebSocket 连接实时监控任务执行过程，当接收到executed类型的消息时，可获取输出图片名称，结合图片在线预览功能实现实时出图的监控。
发起任务的插队：在发起新任务时，通过设置front参数为较大值，保证该任务具有较高的执行优先级，实现插队执行。

English Function Collection
Query the current number of tasks: Query the current number of tasks in ComfyUI and display the result on the page. Send a GET request to the /prompt interface of ComfyUI to obtain task queue information.
Initiate a new task: Read the workflow data from a specified JSON file, modify specific content such as changing strings and randomizing seeds, and then send a POST request to the /prompt interface of ComfyUI to initiate a new task. You can set the number and front parameters to control the task execution order and priority.
Get historical task records: Retrieve historical task records in ComfyUI, including records of all tasks and individual tasks. Achieve this by sending GET requests to the /history and /history/{prompt_id} interfaces.
Get model configuration information: Obtain configuration information of models (such as LoRA, Checkpoints, etc.) in ComfyUI. Send a GET request to the /models/{folder_name} interface to get the information.
Get component information: Retrieve detailed information of each component in ComfyUI. You can query by component name or get information of all components. Send a GET request to the /object_info/{component_name} interface. If no component name is specified, information of all components will be returned.
Upload images or masks: Support uploading images or masks to ComfyUI, and relevant parameters can be set during uploading. Create a FormData object, add the image or mask to it, and then send a POST request to the /upload/image or /upload/mask interface.
Cancel the queue and the current task: Provide the function to cancel the task queue and the currently executing task in ComfyUI. Cancel the queue by sending a POST request containing the delete field to the /queue interface, and cancel the current task by sending a GET request to the /interrupt interface.
Get currently executing and queued tasks: Obtain information about the tasks currently being executed and in the queue in ComfyUI. Organize the returned data and output the running tasks, pending tasks, and client IDs. Achieve this by sending a GET request to the /queue interface.
Online image preview or get image address: Provide the function of online preview or getting the address of input and output images. Achieve this by appending /view?type={input/output}&filename={file_name} to the ComfyUI address.
Real - time WebSocket connection: Establish a WebSocket connection with ComfyUI to receive real - time messages such as task execution status, queue information, and node progress, and perform corresponding processing and output.
Real - time monitoring (real - time image output): Monitor the task execution process in real - time through the WebSocket connection. When a message of type executed is received, the output image name can be obtained, and real - time image output monitoring can be realized in combination with the online image preview function.
Task 插队: When initiating a new task, set the front parameter to a larger value to ensure that the task has a higher execution priority and achieve queuing up for execution.