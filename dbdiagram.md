// DB DESIGN 

// ! USERS TABLE 

TABLE users {
  id SERIAL [pk, increment]
  created_at TIMESTAMP
  updated_at TIMESTAMP
  username VARCHAR(30)
  bio VARCHAR(400)
  avatar VARCHAR(200)
  phone VARCHAR(25)
  email VARCHAR(40)
  password VARCHAR(50)
  status VARCHAR(15)
}

// ! POSTS TABLE 

TABLE posts {
  id SERIAL [pk, increment]
  created_at TIMESTAMP
  updated_at TIMESTAMP
  url VARCHAR(200)
  user_id INTEGER [ref: > users.id]
  caption VARCHAR(240)
  lat REAL
  lng REAL
}

// ! COMMENTS TABLE 

TABLE comments {
  id SERIAL [pk, increment]
  created_at TIMESTAMP
  updated_at TIMESTAMP
  contents VARCHAR(240)
  user_id INTEGER [ref: > users.id]
  post_id INTEGER [ref: > posts.id]
}

// ! LIKES TABLE

TABLE likes {
  id SERIAL [pk, increment]
  created_at TIMESTAMP
  user_id INTEGER [ref: > users.id]
  post_id INTEGER [ref: > posts.id]
  comment_id INTEGER [ref: > comments.id]
}

// ! TAGS TABLE 

TABLE photo_tags {
  id SERIAL [pk, increment]
  created_at TIMESTAMP
  updated_at TIMESTAMP
  post_id INTEGER [ref: > posts.id]
  user_id INTEGER [ref: > users.id]
  x INTEGER
  y INTEGER
}

TABLE caption_tag {
  id SERIAL [pk, increment]
  created_at TIMESTAMP
  post_id INTEGER [ref: > posts.id]
  user_id INTEGER [ref: > users.id]
}

// ! HASHTAGS TABLE

TABLE hastags {
  id SERIAL [pk, increment]
  created_at TIMESTAMP
  title VARCHAR(20)
}

TABLE hastags_posts {
  id SERIAL [pk, increment]
  hastag_id INTEGER [ref: > hastags.id]
  post_id INTEGER [ref: > posts.id]
}

// ! FOLLOWERS TABLE 

TABLE followers {
  id SERIAL [pk, increment]
  created_at TIMESTAMP
  leader_id INTEGER [ref: > users.id]
  follower_id INTEGER [ref: > users.id]
}
```