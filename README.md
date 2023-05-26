# RunTimeNotifactionpermission

## Enable Notification Runtime Permission in Android 13



  ContextCompat.checkSelfPermission(   
                    this, POST_NOTIFICATIONS  
                ) == PackageManager.PERMISSION_GRANTED -> {  
                    // You can use the API that requires the permission.  
                    Log.e(TAG, "onCreate: PERMISSION GRANTED")  
                    sendNotification(this)  
                }  
                shouldShowRequestPermissionRationale(POST_NOTIFICATIONS) -> {  
                    Snackbar.make(  
                        findViewById(R.id.shownotifaction),  
                        "Notification blocked",  
                        Snackbar.LENGTH_LONG  
                    ).setAction("Settings") {  
                        // Responds to click on the action  
                        val intent = Intent(Settings.ACTION_APPLICATION_DETAILS_SETTINGS)  
                        intent.addFlags(Intent.FLAG_ACTIVITY_NEW_TASK)  
                        val uri: Uri = Uri.fromParts("package", packageName, null)  
                        intent.data = uri  
                        startActivity(intent)  
                    }.show()  
                }  
                else -> {  
                    // The registered ActivityResultCallback gets the result of this request  
                    requestPermissionLauncher.launch(  
                        POST_NOTIFICATIONS  
                    )  
                }  
