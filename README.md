# ToastificacionFlutterFlow
This notification widget provides a flexible, visually appealing way to display alerts in your Flutter app.
This notification widget allows you to display custom alerts in various positions on the screen with different styles and effects. Ideal for enhancing user experience, the widget supports customizable positioning, styles, notification types, and additional effects, such as animations and progress bars.

###  Features

This notification widget allows you to display custom alerts in various positions on the screen with different styles and effects. Ideal for enhancing user experience, the widget supports customizable positioning, styles, notification types, and additional effects, such as animations and progress bars.

### Instructions:

##### # Parameters:

toastTitle (String?): Title of the notification. Default is "Notification" if not provided.
toastDescription (String): Description message for the notification.
toastType (String): Type of notification, which determines its color and icon. Options are:
info
warning
error
success
toastStyle (String): Style of the notification’s appearance. Options include:
fillColored
flat
minimal
flatColored
toastPosition (String): Location on the screen for the notification. Possible values are:
Top: topLeft, topCenter, topRight
Center: centerLeft, center, centerRight
Bottom: bottomLeft, bottomCenter, bottomRight
applyBlurEffect (bool): Enables a background blur effect behind the notification.
Example Usage:

### Customization Options:

Icon and Progress Bar: The notification includes an icon and progress bar by default.
Animation: The notification animates with a smooth scale transition.
This widget is designed for simple integration into any app, providing an engaging way to notify users with minimal setup.


    
    import 'package:toastification/toastification.dart';
    //NOTE: add this dependencies -> toastification: ^2.3.0
    
    Future<void> customToastification(
      BuildContext context,
      String? toastTitle,
      String toastDescription,
      String toastType,
      String toastStyle,
      String toastPosition,
      bool applyBlurEffect,
    ) async {
      String titulo = toastTitle ?? "Notification";
    
      ToastificationType type;
      switch (toastType.toLowerCase()) {
        case 'info':
          type = ToastificationType.info;
          break;
        case 'warning':
          type = ToastificationType.warning;
          break;
        case 'error':
          type = ToastificationType.error;
          break;
        case 'success':
        default:
          type = ToastificationType.success;
          break;
      }
    
      ToastificationStyle style;
      switch (toastStyle.toLowerCase()) {
        case 'fillcolored':
          style = ToastificationStyle.fillColored;
          break;
        case 'flat':
          style = ToastificationStyle.flat;
          break;
        case 'minimal':
          style = ToastificationStyle.minimal;
          break;
        case 'flatcolored':
        default:
          style = ToastificationStyle.flatColored;
          break;
      }
    
      Alignment alignment;
      switch (toastPosition) {
        case 'topLeft':
          alignment = Alignment.topLeft;
          break;
        case 'topCenter':
          alignment = Alignment.topCenter;
          break;
        case 'topRight':
          alignment = Alignment.topRight;
          break;
        case 'centerLeft':
          alignment = Alignment.centerLeft;
          break;
        case 'center':
          alignment = Alignment.center;
          break;
        case 'centerRight':
          alignment = Alignment.centerRight;
          break;
        case 'bottomLeft':
          alignment = Alignment.bottomLeft;
          break;
        case 'bottomCenter':
          alignment = Alignment.bottomCenter;
          break;
        case 'bottom-right':
        default:
          alignment = Alignment.bottomRight;
          break;
      }
    
      toastification.show(
        context: context,
        type: type,
        style: style,
        title: Text(titulo),
        description: Text(toastDescription),
        alignment: alignment, // Usa la posición basada en el parámetro
        autoCloseDuration: const Duration(seconds: 4),
        animationBuilder: (
          context,
          animation,
          alignment,
          child,
        ) {
          return ScaleTransition(
            scale: animation,
            child: child,
          );
        },
        icon: Icon(Icons.notifications),
        borderRadius: BorderRadius.circular(12.0),
        boxShadow: [
          BoxShadow(
            color: Colors.black26,
            blurRadius: 10,
            offset: Offset(0, 4),
          ),
        ],
        showProgressBar: true,
        dragToClose: true,
        applyBlurEffect: applyBlurEffect,
      );
    }

###End
