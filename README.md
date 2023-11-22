
# ACL-permission-recourses-roles-module-user-management-
aqsa ameer
BSEEN1E02006

class Permission:
    def __init__(self, name):
        self.name = name

class Resource:
    def __init__(self, name):
        self.name = name

class Role:
    def __init__(self, name):
        self.name = name
        self.permissions = []

    def add_permission(self, permission):
        self.permissions.append(permission)

class User:
    def __init__(self, username):
        self.username = username
        self.roles = []

    def add_role(self, role):
        self.roles.append(role)

class AccessControlList:
    def __init__(self):
        self.permissions = []
        self.resources = []
        self.roles = []

    def add_permission(self, permission):
        self.permissions.append(permission)

    def add_resource(self, resource):
        self.resources.append(resource)

    def add_role(self, role):
        self.roles.append(role)

# Example Usage:
acl = AccessControlList()

read_permission = Permission("read")
write_permission = Permission("write")

course_resource = Resource("course")
assignment_resource = Resource("assignment")

student_role = Role("student")
admin_role = Role("admin")

student_role.add_permission(read_permission)
admin_role.add_permission(read_permission)
admin_role.add_permission(write_permission)

acl.add_permission(read_permission)
acl.add_permission(write_permission)

acl.add_resource(course_resource)
acl.add_resource(assignment_resource)

acl.add_role(student_role)
acl.add_role(admin_role)

# Create a user and assign roles
user1 = User("user1")
user1.add_role(student_role)

# Check user permissions
for role in user1.roles:
    print(f"User {user1.username} has permissions:")
    for permission in role.permissions:
        print(permission.name)
