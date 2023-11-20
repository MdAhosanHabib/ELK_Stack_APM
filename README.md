## Elasticsearch APM with fleet and elastic-agent
<img width="531" alt="9" src="https://github.com/MdAhosanHabib/ELK_Stack_APM/assets/43145662/b9c2a086-cff2-45fd-8b0e-2fe453fb43fd">


```bash
https://www.youtube.com/watch?v=UHQrOdwUg68&t=857s
https://www.elastic.co/guide/en/elasticsearch/reference/current/rpm.html
https://www.elastic.co/guide/en/fleet/8.11/add-fleet-server-on-prem.html

--set on each host almalinux 9
[root@elk ~]# hostnamectl set-hostname elk.kibana.com
[root@elk ~]# hostnamectl set-hostname fleet.elk.com
[root@elk ~]# hostnamectl set-hostname agent.elk.com

#####Elastic_Kibana#####
--on elk node
[root@elk ~]# cat /etc/hosts
127.0.0.1   localhost localhost.localdomain localhost4 localhost4.localdomain4
::1         localhost localhost.localdomain localhost6 localhost6.localdomain6
192.168.0.103 elk.kibana.com elk
192.168.0.106 fleet.elk.com fleet
192.168.0.107 agent.elk.com agent
[root@elk elk_stack]# dnf install telnet wget net-tools curl java -y
[root@elk ~]# java -version
[root@elk ~]# mkdir /elk_stack/
[root@elk ~]# cd /elk_stack/
[root@elk elk_stack]# wget https://artifacts.elastic.co/downloads/elasticsearch/elasticsearch-8.11.1-x86_64.rpm
[root@elk elk_stack]# rpm -ivh elasticsearch-8.11.1-x86_64.rpm
[root@elk elk_stack]# systemctl daemon-reload
[root@elk elk_stack]# systemctl enable elasticsearch.service
[root@elk elk_stack]# systemctl start elasticsearch.service

--kibana download from kibana-8.11.1-x86_64.rpm https://www.elastic.co/downloads/kibana
[root@elk elk_stack]# ll
-rw-r--r-- 1 root root 630601103 Nov 13 19:39 elasticsearch-8.11.1-x86_64.rpm
-rw-r--r-- 1 root root 317639847 Nov 19 16:23 kibana-8.11.1-x86_64.rpm
[root@elk elk_stack]# rpm -ivh kibana-8.11.1-x86_64.rpm
[root@elk elk_stack]# vi /etc/kibana/kibana.yml
    server.port: 5601
    server.host: "192.168.0.103"
[root@elk elk_stack]# systemctl enable kibana
[root@elk elk_stack]# systemctl start kibana
[root@elk elk_stack]# /usr/share/elasticsearch/bin/elasticsearch-reset-password -u kibana_system
This tool will reset the password of the [kibana_system] user to an autogenerated value.
The password will be printed in the console.
Please confirm that you would like to continue [y/N]y
Password for the [kibana_system] user successfully reset.
New value: xKWz4CnLkUvngQ9n+yPl
[root@elk elk_stack]#
```

<img width="960" alt="1" src="https://github.com/MdAhosanHabib/ELK_Stack_APM/assets/43145662/5dd9103e-8bcd-4e2b-92d6-9261cfa336a0">
<img width="960" alt="2" src="https://github.com/MdAhosanHabib/ELK_Stack_APM/assets/43145662/350c9ccd-38d4-408a-962d-82c8c531b0e4">
<img width="960" alt="3" src="https://github.com/MdAhosanHabib/ELK_Stack_APM/assets/43145662/e99728ef-1f6f-4929-b241-d040376cff13">

```bash
[root@elk elk_stack]# /usr/share/kibana/bin/kibana-verification-code
Your verification code is:  121 006
[root@elk elk_stack]# 
```

<img width="960" alt="4" src="https://github.com/MdAhosanHabib/ELK_Stack_APM/assets/43145662/0936016e-2c2c-4c8d-8bd3-88df37d6a60d">

```bash
[root@elk elk_stack]# /usr/share/elasticsearch/bin/elasticsearch-reset-password -u elastic
This tool will reset the password of the [elastic] user to an autogenerated value.
The password will be printed in the console.
Please confirm that you would like to continue [y/N]y
Password for the [elastic] user successfully reset.
New value: +QYvYK5vWZ5g7PJ_HSzY
[root@elk elk_stack]#
```

<img width="960" alt="5" src="https://github.com/MdAhosanHabib/ELK_Stack_APM/assets/43145662/d3621ec3-ab62-44f1-96de-def667cdbdaf">

After this, click at “my own”.

<img width="960" alt="6" src="https://github.com/MdAhosanHabib/ELK_Stack_APM/assets/43145662/df028119-4a43-411b-8cb4-5158afbd2cb4">
<img width="960" alt="7" src="https://github.com/MdAhosanHabib/ELK_Stack_APM/assets/43145662/cffe3ef0-2a9a-4a74-b1b1-359189c2c1e5">
<img width="960" alt="8" src="https://github.com/MdAhosanHabib/ELK_Stack_APM/assets/43145662/4806c4ea-d416-472e-85dc-1d8140c6a3ec">
<img width="531" alt="9" src="https://github.com/MdAhosanHabib/ELK_Stack_APM/assets/43145662/f33966a4-d212-4e65-bfbc-9cf31b933a3d">
<img width="489" alt="10" src="https://github.com/MdAhosanHabib/ELK_Stack_APM/assets/43145662/64c2fd55-73f1-42d0-84eb-02fec199564d">
<img width="960" alt="11" src="https://github.com/MdAhosanHabib/ELK_Stack_APM/assets/43145662/49fb9057-5fa7-4e11-a39e-812629b0e980">
<img width="960" alt="12" src="https://github.com/MdAhosanHabib/ELK_Stack_APM/assets/43145662/a57789f6-44f4-4302-a798-593916461fc3">
<img width="960" alt="13" src="https://github.com/MdAhosanHabib/ELK_Stack_APM/assets/43145662/7566a23f-78e7-4f96-930a-39c7fa00005e">
<img width="960" alt="14" src="https://github.com/MdAhosanHabib/ELK_Stack_APM/assets/43145662/30a969a2-f795-458b-a722-fc60d9fa7a45">
<img width="960" alt="15" src="https://github.com/MdAhosanHabib/ELK_Stack_APM/assets/43145662/aa8ffed9-e110-414a-9f15-cd5dee3b39ed">

```bash
--Generate a service token
AAEAAWVsYXN0aWMvZmxlZXQtc2VydmVyL3Rva2VuLTE3MDA0MTU4ODU1ODg6MWNqNk5rMkVTT0dUMmEwdWQyODRJUQ 
```

<img width="960" alt="16" src="https://github.com/MdAhosanHabib/ELK_Stack_APM/assets/43145662/a7719eef-de8a-47cd-a7b7-1d29a4eee3eb">
<img width="960" alt="17" src="https://github.com/MdAhosanHabib/ELK_Stack_APM/assets/43145662/5f0fdd82-78ed-4b51-bf40-261a0b4a9898">

```bash
--set on fleet OS
[root@fleet ~]# mkdir /root/ca
[root@fleet ~]# cd /root/ca

[root@elk elk_stack]# mkdir /elk_stack/ca
[root@elk elk_stack]# cd /elk_stack/ca
[root@elk ca]# dnf install openssl -y
[root@elk ca]# openssl genpkey -algorithm RSA -out ca.key
[root@elk ca]# openssl req -x509 -new -key ca.key -out ca.crt -days 36500
Country Name (2 letter code) [XX]:BD
State or Province Name (full name) []:Dhaka
Locality Name (eg, city) [Default City]:Dhaka
Organization Name (eg, company) [Default Company Ltd]:ITCL
Organizational Unit Name (eg, section) []:DevOps
Common Name (eg, your name or your server's hostname) []:elk
Email Address []:ahosan@example.com
[root@elk ca]#
/usr/share/elasticsearch/bin/elasticsearch-certutil cert \
  --name fleet-server \
  --ca-cert /elk_stack/ca/ca.crt \
  --ca-key /elk_stack/ca/ca.key \
  --dns fleet.elk.com \
  --ip 192.168.0.106 \
  --pem
[root@elk ca]# ll /usr/share/elasticsearch/certificate-bundle.zip
-rw------- 1 root root 2698 Nov 19 23:55 /usr/share/elasticsearch/certificate-bundle.zip
[root@elk ca]# mv /usr/share/elasticsearch/certificate-bundle.zip .
[root@elk ca]# ll
-rw-r--r-- 1 root root 1403 Nov 19 23:53 ca.crt
-rw------- 1 root root 1704 Nov 19 23:51 ca.key
-rw------- 1 root root 2698 Nov 19 23:55 certificate-bundle.zip
[root@elk ca]# dnf install unzip -y
[root@elk ca]# unzip -q certificate-bundle.zip
[root@elk ca]# cd fleet-server
[root@elk fleet-server]# ll
-rw-r--r-- 1 root root 1298 Nov 19 23:55 fleet-server.crt
-rw-r--r-- 1 root root 1675 Nov 19 23:55 fleet-server.key
[root@elk fleet-server]# pwd
/elk_stack/ca/fleet-server
[root@elk fleet-server]# cd ..
[root@elk ca]# scp -r . root@192.168.0.106:/root/ca


########Fleet Server########
--Generate a service token
AAEAAWVsYXN0aWMvZmxlZXQtc2VydmVyL3Rva2VuLTE3MDA0MTU4ODU1ODg6MWNqNk5rMkVTT0dUMmEwdWQyODRJUQ

[root@fleet fleet-server]# pwd
/root/ca/fleet-server
[root@fleet fleet-server]# ll
total 8
-rw-r--r-- 1 root root 1298 Nov 20 00:06 fleet-server.crt
-rw-r--r-- 1 root root 1675 Nov 20 00:06 fleet-server.key
[root@fleet fleet-server]#

curl -L -O https://artifacts.elastic.co/downloads/beats/elastic-agent/elastic-agent-8.11.1-x86_64.rpm
sudo rpm -vi elastic-agent-8.11.1-x86_64.rpm

sudo elastic-agent enroll --url=https://192.168.0.106:8220 \
  --fleet-server-es=https://192.168.0.103:9200 \
  --fleet-server-service-token=AAEAAWVsYXN0aWMvZmxlZXQtc2VydmVyL3Rva2VuLTE3MDA0MTU4ODU1ODg6MWNqNk5rMkVTT0dUMmEwdWQyODRJUQ \
  --fleet-server-policy=fleet-server-policy \
  --fleet-server-es-ca-trusted-fingerprint=9d07dc00fa36c52007e5569d68e27313cdd3a7e54f075b8f32ffed7d54df4c80 \
  --certificate-authorities=/root/ca/ca.crt \
  --fleet-server-cert=/root/ca/fleet-server/fleet-server.crt \
  --fleet-server-cert-key=/root/ca/fleet-server/fleet-server.key \
  --fleet-server-port=8220
sudo systemctl enable elastic-agent
sudo systemctl start elastic-agent
```

<img width="960" alt="18" src="https://github.com/MdAhosanHabib/ELK_Stack_APM/assets/43145662/9bb6c5b5-36c2-45e9-9301-11940fd2ea52">
<img width="960" alt="19" src="https://github.com/MdAhosanHabib/ELK_Stack_APM/assets/43145662/305c4077-9424-42bf-a732-7eb85704c66c">
<img width="960" alt="20" src="https://github.com/MdAhosanHabib/ELK_Stack_APM/assets/43145662/bfa9a2e8-3fdf-47c2-b2f9-fa845cc0888b">
<img width="960" alt="21" src="https://github.com/MdAhosanHabib/ELK_Stack_APM/assets/43145662/374d89cc-2238-4390-8495-f9ac14d88ad1">
<img width="960" alt="22" src="https://github.com/MdAhosanHabib/ELK_Stack_APM/assets/43145662/cfbd3f14-8045-4a29-9577-15f9e42b8c09">
<img width="960" alt="23" src="https://github.com/MdAhosanHabib/ELK_Stack_APM/assets/43145662/efd5b991-fc0a-4d1b-ae27-7f1b8fc7c5b6">
<img width="960" alt="24" src="https://github.com/MdAhosanHabib/ELK_Stack_APM/assets/43145662/190d6367-1d84-46d4-9d5e-4614f43ffd3d">

```bash
#####On APP host#####
[root@agent ~]# mkdir /root/ca/
[root@agent ~]# cd /root/ca/

--on fleet host
[root@elk ca]# scp -r /root/ca/elastic-agent-8.11.1-x86_64.rpm root@192.168.0.107:/root/ca/

#curl -L -O https://artifacts.elastic.co/downloads/beats/elastic-agent/elastic-agent-8.11.0-x86_64.rpm
sudo rpm -vi elastic-agent-8.11.1-x86_64.rpm

--on elk host
[root@elk ca]# scp -r /elk_stack/ca root@192.168.0.107:/root/ca

elastic-agent enroll --url=https://192.168.0.106:8220 --enrollment-token=UG13dzY0c0JrOGRQNHhqaFJIeFQ6c2NYOG5tNnZTeXVjUTNJTVB1dXdzZw== \
--certificate-authorities=/root/ca/ca/ca.crt \
--fleet-server-cert=/root/ca/ca/fleet-server/fleet-server.crt \
--fleet-server-cert-key=/root/ca/ca/fleet-server/fleet-server.key

sudo systemctl enable elastic-agent 
sudo systemctl start elastic-agent
```

<img width="960" alt="25" src="https://github.com/MdAhosanHabib/ELK_Stack_APM/assets/43145662/853a2f95-12b5-42b2-9edb-58f284a25b35">

```bash
#################Sample Python_FastAPI app################
[root@agent ca]# cd /root/ca
[root@agent ca]# sudo dnf install python3 -y
[root@agent ca]# dnf install pip
[root@agent ca]# pip3 install fastapi uvicorn
[root@agent ca]# pip install elastic-apm
[root@agent ca]# vi /root/ca/main.py

from fastapi import FastAPI
from elasticapm.contrib.starlette import make_apm_client, ElasticAPM

app = FastAPI()

#Configure the Elastic APM client
apm = make_apm_client(
    app_name="APMbyPython",  # Set your app name
    server_url="http:// 127.0.0.1:8200",  # Set your APM server URL
)

#Add the APM middleware to your FastAPI app
app.add_middleware(ElasticAPM, client=apm)

@app.get("/")
def read_root():
    # Your FastAPI route code
    return {"ITCL": "APM_ELK_TEST"}

[root@agent ~]# cd /root/ca/
[root@agent ca]# uvicorn main:app --reload --host 192.168.0.107 --port 8000
```

<img width="960" alt="26" src="https://github.com/MdAhosanHabib/ELK_Stack_APM/assets/43145662/6f8f48ca-8ad1-4b80-b123-6ae03532b000">
<img width="960" alt="27" src="https://github.com/MdAhosanHabib/ELK_Stack_APM/assets/43145662/2b65747f-2efb-453b-bea3-c279ae6a5f46">

#### Should more explore in future…
