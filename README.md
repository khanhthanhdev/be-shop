# be-shop
## Summary api category

- branch: route/cart

## USE

1. create cart

- method: POST
- data:
  {
  "cartItemId":"601015e86e989f46b051b0f0",
  "quantity":1,
  "size":39
  }

- url: localhost:5000/cart/create
- response:
  {
  "status": "success",
  "message": "Ban da mua hang thanh cong",
  "totalProducts": 4
  }

2. update cart

- mehtod: POST
- url: localhost:5000/cart/update/Giay-XSPORT-ADD-Alphabounce-Beyond-REP?size=38&quantity=6
- response:

3. get cart by user

- method: GET
- url: localhost:5000/cart
- response:

4. delete cart

- method: DELETE
- url: localhost:5000/cart/6019dd8d4c09e525d80834c4
- response:

## Summary api category

- branch: route/category

- body
  - name
  - parentId: có hoặc ko, không có = main category, có = sub category
- params
  - id của category

## USE

1. get all categories

- url: localhost:5000/category
- api trả về 2 kiểu
  - list của các category
- response
  - status: "success",
    category: {
    {
    "\_id": "600bcf1ab4df7b2184619798",
    "name": "category 1",
    "slug": "category-1"
    },
    {
    "\_id": "600bcf39b4df7b2184619799",
    "name": "category 1 sub 1 update",
    "slug": "category-1-sub-1-update",
    "parentId": "600bcf1ab4df7b2184619798"
    }
  - group các category dựa vào trường parentId
- response
  - status: "success",
    categories: {
    "\_id": "600bcf1ab4df7b2184619798",
    "name": "category 1",
    "slug": "category-1",
    "children": [
    {
    "\_id": "600bcf39b4df7b2184619799",
    "name": "category 1 sub 1 update",
    "parentId": "600bcf1ab4df7b2184619798",
    "slug": "category-1-sub-1-update",
    "children": []
    }
    ]
    },

2. create category

- url: localhost:5000/category/create
- body bao gồm : name và parentId (có hoặc không)
- response
  - status: "success",
    category: newCategory,

3. update category

- url: localhost:5000/category/:id
- body bao gồm : name và parentId (có hoặc không)
- response
  - status: "success",
    message: "Update category successful",

4. delete category

- url: localhost:5000/category/:id
- body bao gồm : name và parentId (có hoặc không)
- response
  - status: "success",
    message: "Delete category successful",

## Summary api category

## USE

1. get all products

- method : GET
- url: localhost:5000/products/?search=abc
  - nếu không có search thì lất tất cả product, có phân trang

2. get products by slug

- method: GET
- url: localhost:5000/products/Giay-Vans/?rating=5&minPrice=495000&maxPrice=550000&page=1&limit=20
  - rating: filter theo rating,
  - minPrice, maxPrice: filter theo price
  - page, limit => phân trang

2. get initial data

- method: GET
- url: localhost:5000/products/initial-data
  - lấy dữ liệu ban đầu

3. get product detail

- method: GET
- url: localhost:5000/products/detail/Giay-The-Thao-Adi.das-Superstar-Trang-mui-so-F1
  - lấy theo slug của product

## Summary api user

- src: middleware/auth

- branch: route/user/update-auth

- tạo một số middleware cho việc signin và user role

- tạo router refresh-token với end point: localhost:2000/user/refresh-token

  - reftoken : có thể gửi trong body hoặc params

- chú ý có một số chỉnh sửa trong file controller user.js cũ.

## USE

1. change function auth => requireSignin
2. create:

- userProfile: for get profile của user đã signin đặt sau requireSignin
- userRequire hoặc adminRequire : kiểm soát quyền của user, đặt sau userProfile

- ex: router.post("/create", signinRequire, userProfile, adminRequire, addCategory);

3. refresh-token => trả về token và refresh token mới

## Summary api category

- branch: route/order

## USE

1. create order

- method: POST
- data:
  {
  "cardId":"601cafcb670b57112c84ca4a",// id của cart
  "cart": [ // các product từ cart chuyển thành format này nhé
  {
  "productId": "601015e86e989f46b051b0f0",
  "payablePrice": 430000,
  "purchaseQty": 1
  },
  {
  "productId": "601015e86e989f46b051b0f0",
  "payablePrice": 430000,
  "purchaseQty": 1
  }
  ],
  "name": "kent bui 123",
  "phone": "012345678",
  "city": "ha noi",
  "town": "cau giay",
  "address": "1234567890",
  "fee": 30000, // hiện tại đang để cái này cố định, khi nào làm phần địa chỉ thì cho vào, và tính toán khi up địa chỉ thành công, hiện tại đang bỏ qua
  "totalAmount": 860000 // cai nay tinh toan o local luon nhe
  }

- url: localhost:5000/order/create
- response:

2. update order:// sau này phat triển thêm, khi các đơn hàng cập nhật trạng thái

3. get all order by user => for admin

- method: GET
- url: localhost:5000/order
- response:

4. delete order

- method: DELETE
- xóa 1 đơn hàng trong list đặt hàng của khách hàng
- url: localhost:5000/order/601cb37c80060a18fcc645d6
- response:

5. get an order

- method: GET
- xem 1 đơn hàng
- url: localhost:5000/order/601bc330f2279420e02f35e7
- response


