# macro-excel-restapi-sms-send
Macro Script (SMS Send using REST API)
Sample Examle: 

'OnnoRokom SMS Excel Macro Script
'Bulk SMS Proving only for Bangladesh
'Rest API Calling Example using Macro
'Function Call Button Click
Sub Macro1()
    'Function Call
    Call SMS
End Sub

Public Function SMS()
    Dim DataToSend As String
    'XML Object Initilization
    Dim objXML As Object
    'SMS API Key
    Dim apiKey As String
    'Mobile Number
    Dim mobileNumber As String
    'SMS TEXT
    Dim smsText As String
    'SMS Option Perameter
    Dim op As String
    'SMS TYPE
    Dim smsType As String
    'SMS Request URL
    Dim URL As String
    'SMS Masking
    Dim maskName As String
    'SMS Campaign
    Dim campaignName As String
    'API KEY OnnoRokomSMS Panel
    apiKey = ""
    'Get Mobile Number from WorkBook
    mobileNumber = Range("$A$1").Value
    'TEXT Message
    smsText = "Your TEXT Message here..."
    'Option Method Name
    op = "NumberSms" 'OneToOne and OneToMany
    'SMS Type
    smsType = "TEXT"
    'Request URL
    URL = "https://api2.onnorokomsms.com/HttpSendSms.ashx?"
    'HTTP Request Create
    Set objXML = CreateObject("MSXML2.serverXMLHTTP")
    'Request Type
    objXML.Open "POST", URL, False
    'Request Content Header
    objXML.setRequestHeader "Content-Type", "application/x-www-form-urlencoded"
    'Send Send Create Full URL
    objXML.send "op=" + op + "&apiKey=" + apiKey + "&type=" + smsType + "&mobile=" + mobileNumber + "&smsText=" + smsText + "&maskName=&campaignName"
    
    'Response Message
    If Len(objXML.responseText) > 0 Then
            MsgBox objXML.responseText
    End If

End Function
