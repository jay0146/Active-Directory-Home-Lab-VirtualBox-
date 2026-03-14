$PASSWORD_FOR_USERS = "Password1"
$NUMBER_OF_ACCOUNTS_TO_CREATE = 1000
$OUTPUT_FILE = "names.txt"

function Generate-Random-Name {
    $consonants = @('b','c','d','f','g','h','j','k','l','m','n','p','q','r','s','t','v','w','x','z')
    $vowels = @('a','e','i','o','u','y')
    $nameLength = Get-Random -Minimum 3 -Maximum 7
    $count = 0
    $name = ""

    while ($count -lt $nameLength) {
        if (($count % 2) -eq 0) {
            $name += $consonants[(Get-Random -Minimum 0 -Maximum $consonants.Count)]
        }
        else {
            $name += $vowels[(Get-Random -Minimum 0 -Maximum $vowels.Count)]
        }
        $count++
    }

    return $name.Substring(0,1).ToUpper() + $name.Substring(1).ToLower()
}

if (Test-Path $OUTPUT_FILE) {
    Remove-Item $OUTPUT_FILE
}

$password = ConvertTo-SecureString $PASSWORD_FOR_USERS -AsPlainText -Force

$count = 1
while ($count -le $NUMBER_OF_ACCOUNTS_TO_CREATE) {

    $firstName = Generate-Random-Name
    $lastName = Generate-Random-Name
    $username = ($firstName + "." + $lastName).ToLower()

    Write-Host "Creating user: $username" -BackgroundColor Black -ForegroundColor Cyan

    Add-Content -Path $OUTPUT_FILE -Value $username

    New-ADUser `
        -AccountPassword $password `
        -GivenName $firstName `
        -Surname $lastName `
        -DisplayName $username `
        -Name $username `
        -SamAccountName $username `
        -UserPrincipalName "$username@yourdomain.local" `
        -EmployeeID $username `
        -PasswordNeverExpires $true `
        -Path "OU=_EMPLOYEES,$(([ADSI]`"").distinguishedName)" `
        -Enabled $true

    $count++
}
