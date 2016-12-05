# gitlab openshift cas单点登录和ldap认证两种模式

git clone https://github.com/asiainfoLDP/gitlab-cas-ldap-openshift.git

1 ldap认证：


```

cd gitlab-cas-ldap-openshift

# 创建ldap或者使用已有ldap
oc create -f ldap-dc.yaml
oc create -f ldap-svc.yaml

# 创建数据库
oc create -f postgresql-dc.yaml
oc create -f redis-dc.yaml

# 创建gitlab-ldap
oc create -f gitlab-ldap-dc.yaml

# 注：以上注意修改数据库、及其他服务的账号密码

# 创建 service
 oc create -f all-svc.yaml

```
1.1 创建路由：

```
oc expose svc git --hostname=< namespaces >
```

2 cas 单点登录

```
cd gitlab-cas-ldap-openshift

# 创建数据库
oc create -f postgresql-dc.yaml
oc create -f redis-dc.yaml

# 创建gitlab-cas
oc create -f gitlab-cas-dc.yaml   # cas域名处不要以"/"结尾
# 注：以上注意修改数据库、及其他服务的账号密码

# 创建 service
 oc create -f all-svc.yaml

```
2.1 创建路由：
```
oc expose svc git --hostname=< namespaces >
```

3 需要持久化的服务

postgresql ldap git

4 操作流程：
