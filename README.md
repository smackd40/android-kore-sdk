# Overview
    This SDK allows you to talk to Bots over a web socket.

# Prerequisites
    - SDK app credentials (Create your SDk app in bot admin console to aquire the client id and client secret.
    - jwt assertion generation methodology. ex: service which will be used in the assertion function injected as part of obtaining the connection.
    
# Running the Demo app
    Download or clone the repository.
    Import the project.
    Run the app.

# Integrating into your app
#### 1. Create BotClient object
    Create BotClient object providing context.
    BotClient botClient = new BotClient(context);
    
#### 2. Implement SocketConnectionListener
    Implement this interface to receive callbacks
    SocketConnectionListener socketConnectionListener = new SocketConnectionListener() {
        ...
    };
    
#### 3. Initializing the RTM client
    String accessToken = "Y6w*******************";
    String chatBot = "My Bot";
    String taskBotId = "st-**************";
    botClient.connectAsAuthenticatedUser(accessToken, chatBot, taskBotId, socketConnectionListener);
    
#### 4. Send message
    botClient.sendMessage("Tweet hello")
    
#### 5. Listen to events
    Listen to events in socketConnectionListener.
    
    @Override
    public void onOpen() {
    }
    @Override
    public void onClose(WebSocket.WebSocketConnectionObserver.WebSocketCloseNotification code, String reason) {
    }
    @Override
    public void onTextMessage(String payload) {
    }
    @Override
    public void onRawTextMessage(byte[] payload) {
    }
    @Override
    public void onBinaryMessage(byte[] payload) {
    }
    
#### 6. Subscribe to push notifications
    PushNotificationRegister pushNotificationRegister =  new PushNotificationRegister(requestListener);
    pushNotificationRegistrar.registerPushNotification(Context context, String userId, String accessToken, String deviceId);
    
#### 7. Unsubscribe to push notifications
    PushNotificationRegister pushNotificationRegister =  new PushNotificationRegister(requestListener);
    pushNotificationRegister.unsubscribePushNotification(Context context, String accessToken, String deviceId);

#### 8. Anonymous user login
    String clientId = "YOUR_SDK_CLIENTID";
    botClient.connectAsAnonymousUser(String clientId, SocketConnectionListener socketConnectionListener)
    
#### 9. Disconnect
    Invoke to disconnect previous socket connection upon closing Activity/Fragment or upon destroying view.
    
    botClient.disconnect();
    
    



























License
----
Copyright © Kore, Inc. MIT License; see LICENSE for further details.



 
