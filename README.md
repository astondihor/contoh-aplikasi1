Contoh Aplikasi1
================

Hanya sebuah contoh aplikasi yang saya buat menggunakan PHP Laravel 4.1.x [catatan](./docs/catatan.md)

Ini dimaksudkan untuk memberikan gambaran kepada yang membutuhkan sebuah aplikasi yang memiliki RBAC (Role Based Access Control).

Masih banyak kekurangan dalam aplikasi ini, ini masih dalam tahap belajar. Semoga dapat memberikan sesuatu kepada pengunjung. Apapun itu. :)

Untuk sementara dapat dilihat demo disini: [astondihor.animousconsulting.com](http://astondihor.animousconsulting.com)


Database
--------

Database menggunakan MySQL.

Database Models
---------------

Download MySQLWorkbench files: [contoh-aplikasi1.mwb](https://github.com/astondihor/contoh-aplikasi1/raw/master/DBModel/contoh-aplikasi1.mwb)

[![Databse Model 1](https://raw.github.com/astondihor/contoh-aplikasi1/master/DBModel/users_roles_throttle_permissions_th.jpg)](https://raw.github.com/astondihor/contoh-aplikasi1/master/DBModel/users_roles_throttle_permissions.jpg)


## Contoh RBAC

User dengan ID: 45
Role: admin (ID: 6)
Permission: Boleh membuka module users semua aksi.

User dengan ID: 46
Role: user (ID: 5)
Permission: Hanya bisa melihat account sendiri, edit profile, change
password.

Table: user
<table>
<tr>
<th>id</th>
<th>username</th>
</tr>
<tr>
<td>45</td>
<td>aston</td>
</tr>
<tr>
<td>46</td>
<td>barak-oh-bama</td>
</tr>
</table>


Table: roles
<table>
  <tr>
    <th>id</th>
    <th>role_name</th>
    <th>inherited</th>
  </tr>
  <tr>
    <td>5</td>
    <td>user</td>
    <td>NULL</td>
  </tr>
  <tr>
    <td>6</td>
    <td>admin</td>
    <td>NULL</td>
  </tr>
</table>

Table: role_user
<table>
<tr>
<th>role_id</th>
<th>user_id</th>
</tr>
<tr>
<td>6</td>
<td>45</td>
</tr>
<tr>
<td>5</td>
<td>46</td>
</tr>
</table>

Table: Permission

<table>
  <thead>
    <tr>
      <th>id</th>
      <th>role_id</th>
      <th>type</th>
      <th>action</th>
      <th>resource</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>1</td>
      <td>6</td>
      <td>allow</td>
      <td>manage</td>
      <td>users</td>
    </tr>
    <tr>
      <td>2</td>
      <td>6</td>
      <td>allow</td>
      <td>view</td>
      <td>users</td>
    </tr>
    <tr>
      <td>3</td>
      <td>6</td>
      <td>allow</td>
      <td>create</td>
      <td>users</td>
    </tr>
    <tr>
      <td>4</td>
      <td>6</td>
      <td>allow</td>
      <td>update</td>
      <td>users</td>
    </tr>
    <tr>
      <td>5</td>
      <td>6</td>
      <td>allow</td>
      <td>delete</td>
      <td>users</td>
    </tr>
    <tr>
      <td>7</td>
      <td>5</td>
      <td>allow</td>
      <td>edit</td>
      <td>profile</td>
    </tr>
  </tbody>
</table>
