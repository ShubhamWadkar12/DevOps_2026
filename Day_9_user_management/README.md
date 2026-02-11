# Day 09 – User & Group Management

## Users Created
- tokyo
- berlin
- professor
- nairobi

## Groups Created
- developers
- admins
- project-team

---

## Task 1: Create Users

useradd -m tokyo  
passwd tokyo  

useradd -m berlin  
passwd berlin  

useradd -m professor  
passwd professor  

Check:
ls /home  

---

## Task 2: Create Groups

groupadd developers  
groupadd admins  

Check:
cat /etc/group | grep developers  
cat /etc/group | grep admins  

---

## Task 3: Add Users to Groups

tokyo → developers  
berlin → developers, admins  
professor → admins  

usermod -aG developers tokyo  
usermod -aG developers,admins berlin  
usermod -aG admins professor  

Check:
groups tokyo  
groups berlin  
groups professor  

---

## Task 4: Shared Folder (developers)

mkdir /opt/dev-project  
chgrp developers /opt/dev-project  
chmod 775 /opt/dev-project  

Check:
ls -ld /opt/dev-project  

Test:
sudo -u tokyo touch /opt/dev-project/a.txt  
sudo -u berlin touch /opt/dev-project/b.txt  

---

## Task 5: Team Workspace

useradd -m nairobi  
passwd nairobi  

groupadd project-team  

usermod -aG project-team nairobi  
usermod -aG project-team tokyo  

mkdir /opt/team-workspace  
chgrp project-team /opt/team-workspace  
chmod 775 /opt/team-workspace  

Test:
sudo -u nairobi touch /opt/team-workspace/x.txt  

---

## What I Learned

- Users work using groups
- Groups control folder access
- chmod fixes permission issues
