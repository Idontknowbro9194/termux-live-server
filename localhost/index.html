<?php
error_reporting(E_ALL); // Enable error reporting for debugging

// Step 1: Generate a temporary email using the Temp-Mail API
function generateRandomString($length = 10) {
    $characters = '0123456789abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ';
    $charactersLength = strlen($characters);
    $randomString = '';
    for ($i = 0; $i < $length; $i++) {
        $randomString .= $characters[rand(0, $charactersLength - 1)];
    }
    return $randomString;
}

// Function to generate a random domain from a predefined list
function getRandomDomain() {
    $domains = ['greencafe24.com', 'tempmail.dev', 'mailinator.com', 'guerrillamail.com'];
    return $domains[array_rand($domains)];
}

// Modified function to generate a temporary email
function generateTempEmail() {
    // Generate a random name and domain
    $randomName = generateRandomString(rand(8, 12)); // Name length between 8 and 12 characters
    $randomDomain = getRandomDomain();

    $url = "https://api.internal.temp-mail.io/api/v3/email/new";
    $data = json_encode(['name' => $randomName, 'domain' => $randomDomain]);
    
    $headers = [
        'User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64)',
        'Content-Type: application/json'
    ];

    $ch = curl_init();
    curl_setopt($ch, CURLOPT_URL, $url);
    curl_setopt($ch, CURLOPT_HTTPHEADER, $headers);
    curl_setopt($ch, CURLOPT_SSL_VERIFYHOST, 0);
    curl_setopt($ch, CURLOPT_SSL_VERIFYPEER, 0);
    curl_setopt($ch, CURLOPT_POST, 1);
    curl_setopt($ch, CURLOPT_POSTFIELDS, $data);
    curl_setopt($ch, CURLOPT_RETURNTRANSFER, 1);
    $response = curl_exec($ch);
    curl_close($ch);

    $json = json_decode($response, true);
    return $json['email'] ?? 'error@example.com';
}


// Step 2: Fetch OTP from the temporary email inbox (Retry mechanism added)
function fetchOTP($email, $maxRetries = 5) {
    $inboxUrl = "https://api.internal.temp-mail.io/api/v3/email/$email/messages";
    $otp = ''; // Initialize OTP as empty

    for ($i = 0; $i < $maxRetries; $i++) {
        $ch = curl_init();
        curl_setopt($ch, CURLOPT_URL, $inboxUrl);
        curl_setopt($ch, CURLOPT_SSL_VERIFYHOST, 0);
        curl_setopt($ch, CURLOPT_SSL_VERIFYPEER, 0);
        curl_setopt($ch, CURLOPT_RETURNTRANSFER, 1);
        $response = curl_exec($ch);
        curl_close($ch);

        $json = json_decode($response, true);
        
        // Log the raw response for debugging
        echo "<pre>Raw Email Data: ";
        print_r($json);
        echo "</pre>";

        // Check if emails are returned
        if (is_array($json) && count($json) > 0) {
            // Fetch the latest message (i.e., the one with the highest index)
            $latestMessage = end($json);
            $message = $latestMessage['body_text'] ?? $latestMessage['body'];
            $otp = extractOTPFromMessage($message);
            
            if ($otp) {
                break; // Exit loop if OTP is found
            }
        }
        
        // Sleep for a few seconds before retrying (to wait for the email)
        sleep(5);
    }

    return $otp;
}

// Step 3: Extract OTP from email content (modify this based on actual format)
function extractOTPFromMessage($message) {
    // Log the message content for debugging
    echo "<pre>Email Message: " . htmlentities($message) . "</pre>";

    // Extract a 6-digit OTP from the message
    preg_match('/\b\d{6}\b/', $message, $matches);
    return $matches[0] ?? '';
}

// Step 4: Function to register an account with the OTP, mail, and refer code
function registerAccount($mail, $otp, $refer) {
    $url = "https://www.newbusiness.cc/h5-prod-api/api/register";
    $data = '{"account":"' . $mail . '","captcha":"' . $otp . '","password":"Raj9194@MAD","surePassword":"Raj9194@MAD","inviteCode":"' . $refer . '"}';

    $headers = [
        'Host: www.newbusiness.cc',
        'sec-ch-ua: "Chromium";v="128", "Not;A=Brand";v="24", "Android WebView";v="128"',
        'sec-ch-ua-platform: "Android"',
        'user-agent: Mozilla/5.0 (Linux; Android 14; I2207 Build/UP1A.231005.007) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/128.0.6613.146 Mobile Safari/537.36',
        'content-type: application/json;charset=UTF-8',
        'origin: https://www.newbusiness.cc',
        'referer: https://www.newbusiness.cc/pages/myUser/register/register?inviteCode=' . $refer,
        'Content-length: ' . strlen($data)
    ];

    $ch = curl_init();
    curl_setopt($ch, CURLOPT_URL, $url);
    curl_setopt($ch, CURLOPT_HTTPHEADER, $headers);
    curl_setopt($ch, CURLOPT_SSL_VERIFYHOST, 0);
    curl_setopt($ch, CURLOPT_SSL_VERIFYPEER, 0);
    curl_setopt($ch, CURLOPT_POST, 1);
    curl_setopt($ch, CURLOPT_POSTFIELDS, $data);
    curl_setopt($ch, CURLOPT_RETURNTRANSFER, 1);
    $response = curl_exec($ch);
    curl_close($ch);

    $json = json_decode($response, true);
    return $json['msg'] ?? 'Error occurred during registration.';
}

// Step 5: Main Process - Automatically perform all steps
if (isset($_GET['submit'])) {
    $refer = $_GET['refer'];

    // Generate temporary email
    $tempEmail = generateTempEmail();
    echo "Generated Temporary Email: $tempEmail<br>";

    // Send OTP to the temporary email by initiating the registration process
    $url = "https://www.newbusiness.cc/h5-prod-api/api/verify";
    $data = '{"phone":"' . $tempEmail . '","type":"register"}';

    $headers = [
        'Host: www.newbusiness.cc',
        'sec-ch-ua: "Chromium";v="128", "Not;A=Brand";v="24", "Android WebView";v="128"',
        'sec-ch-ua-platform: "Android"',
        'user-agent: Mozilla/5.0 (Linux; Android 14; I2207 Build/UP1A.231005.007) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/128.0.6613.146 Mobile Safari/537.36',
        'content-type: application/json;charset=UTF-8',
        'origin: https://www.newbusiness.cc',
        'referer: https://www.newbusiness.cc/pages/myUser/register/register?inviteCode=' . $refer,
        'Content-length: ' . strlen($data)
    ];

    $ch = curl_init();
    curl_setopt($ch, CURLOPT_URL, $url);
    curl_setopt($ch, CURLOPT_HTTPHEADER, $headers);
    curl_setopt($ch, CURLOPT_SSL_VERIFYHOST, 0);
    curl_setopt($ch, CURLOPT_SSL_VERIFYPEER, 0);
    curl_setopt($ch, CURLOPT_POST, 1);
    curl_setopt($ch, CURLOPT_POSTFIELDS, $data);
    curl_setopt($ch, CURLOPT_RETURNTRANSFER, 1);
    $response = curl_exec($ch);
    curl_close($ch);

    echo "OTP Request Sent. Waiting for OTP...<br>";

    // Fetch OTP
    $otp = fetchOTP($tempEmail);
    echo "Fetched OTP: $otp<br>";

    // Register account using OTP
    $registrationMessage = registerAccount($tempEmail, $otp, $refer);
    echo "Registration Response: $registrationMessage<br>";

    // Add JavaScript to refresh the page every 3 seconds
    echo "<script>
            setTimeout(function() {
                window.location.reload();
            }, 3000); // Reloads the page every 3 seconds
          </script>";
} else {
    echo "
    <div class='container my-3' style='background-color: #f2f9ff;'>
        <form method='get' class='text-center'>
            <div class='input-group my-4'>
                <span class='input-group-text text-white bg-danger'>Refer Code</span>
                <input type='text' class='form-control' name='refer' placeholder='123456' required>
            </div>
            <input class='btn font-weight-bold btn-info col-6' name='submit' type='submit' value='Submit'>
        </form>
    </div>";
}
?>
