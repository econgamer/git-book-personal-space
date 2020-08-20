# Ansible feat. Nginx - Get the server status with Ansible

#### Materials: [https://docs.ansible.com/ansible/2.5/modules/modules\_by\_category.html](https://docs.ansible.com/ansible/2.5/modules/modules_by_category.html)

ngx: [http://nginx.org/en/docs/http/ngx\_http\_stub\_status\_module.html](http://nginx.org/en/docs/http/ngx_http_stub_status_module.html)

Setting up ngx\_http\_stub\_status\_module:

```
server{

    location = /basic_status{
         stub_status;   
    }

}
```



```text
# Gather status facts from nginx on localhost
- name: get current http stats
  nginx_status_facts:
    url: http://localhost/nginx_status

# Gather status facts from nginx on localhost with a custom timeout of 20 seconds
- name: get current http stats
  nginx_status_facts:
    url: http://localhost/nginx_status
    timeout: 20
```

### Run it

```text
ansible-playbook -i hosts playbook.yml
```

### Cheat Sheet

File Structure:

```text
.
├── hosts
├── playbook.yml
└── roles
    └── my-role
        ├── files
        │   └── test.txt
        └── tasks
            └── main.yml
```

```text
ansible-playbook -i hosts playbook.yml
```

Reference: [https://stackoverflow.com/questions/26732241/ansible-save-registered-variable-to-file](https://stackoverflow.com/questions/26732241/ansible-save-registered-variable-to-file)

