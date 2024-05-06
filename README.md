# 3.1. Original code
![image1](/img/image1.png)
![image2](/img/image2.png)

# 3.2. Add some creativities to the webclient
![image3](/img/image3.png)
![image4](/img/image4.png)
![image5](/img/image5.png)

Pada komponen chat, saya memodifikasi pada function view dengan menambah kode:
```rust
let (user, _) = ctx
            .link()
            .context::<User>(Callback::noop())
            .expect("context to be set");
        let username = user.username.borrow().clone();
```
Dari kode tersebut saya dapat mengambil nama current user yang sedang menggunakan chat dan melakukan modifikasi pada chat bubble current user untuk membedakan dengan user yang lain:

```rust
self.messages.iter().map(|m| {
    let user = self.users.iter().find(|u| u.name == m.from).unwrap();
    let alignment = if m.from.clone() == username.to_string() { "ml-auto bg-gray-200 border-2 border-black" } else { "" };
    html!{
        <div class={format!("flex items-end w-3/6 bg-gray-100 m-8 rounded-tl-lg rounded-tr-lg rounded-br-lg {}", alignment)}>
```
Dari kode tersebut chat bubble current user akan berada di bagian kanan dengan background yang lebih gelap dan memiliki border hitam, menunjukkan nama user dari client tersebut.