FROM microsoft/aspnet:3.5-windowsservercore-ltsc2016
SHELL ["powershell"]
RUN Remove-Website -Name 'Default Web Site'; \
    New-Item -Path 'C:\web-app' -Type Directory; \
    New-Website -Name 'web-app' -PhysicalPath 'C:\web-app' -Port 80 -Force
EXPOSE 80
RUN Set-ItemProperty -Path 'HKLM:\SYSTEM\CurrentControlSet\Services\Dnscache\Parameters' \
    -Name ServerPriorityTimeLimit -Value 0 -Type DWord
#RUN curl https://api.nuget.org/v3/index.json -v
COPY WebSite2 /web-app