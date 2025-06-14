PowerShell
-------------------
# 1. Create a self-signed cert in the user's certificate store
$cert = New-SelfSignedCertificate `
  -DnsName "localhost" `
  -CertStoreLocation "cert:\CurrentUser\My" `
  -FriendlyName "ASP.NET Core Dev Cert"

# 2. Prepare password for export
$pwd = ConvertTo-SecureString -String "p@ssw0rd" -Force -AsPlainText

# 3. Export the certificate to a .pfx file
Export-PfxCertificate `
  -Cert "cert:\CurrentUser\My\$($cert.Thumbprint)" `
  -FilePath "E:\certs\aspnetapp.pfx" `
  -Password $pwd
