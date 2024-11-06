- 👋 Hi, I’m @Ohnstokk3
- 👀 I’m interested in 
- 🌱 I’m currently learning c++
- 💞️ I’m looking to collaborate on c++ projects
- 📫 How to reach me hh71728@gmail.com 

<!---
Ohnstokk3/Ohnstokk3 is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
import okhttp3.*
import okhttp3.WebSocket
import okhttp3.WebSocketListener
import okio.ByteString
import java.util.concurrent.TimeUnit

fun main() {
    val client = OkHttpClient.Builder()
        .readTimeout(0, TimeUnit.MILLISECONDS)
        .writeTimeout(0, TimeUnit.MILLISECONDS)
        .build()

    val request = Request.Builder()
        .url("ws://your_websocket_server_url")
        .build()

    client.newWebSocket(request, object : WebSocketListener() {
        override fun onOpen(webSocket: WebSocket, response: Response) {
            println("Connected to WebSocket server")
            webSocket.send("Hello from Kotlin!")
        }

        override fun onMessage(webSocket: WebSocket, text: String) {
            println("Received message: $text")
        }

        override fun onClosing(webSocket: WebSocket, code: Int, reason: String) {
            println("Connection closed: $code $reason")
        }

        override fun onFailure(webSocket: WebSocket, t: Throwable, response: Response?) {
            println("Connection failure: $t")
        }
    })
}
