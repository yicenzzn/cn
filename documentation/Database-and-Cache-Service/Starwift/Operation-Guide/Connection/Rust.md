# Rust

* tcp 连接

  * 依赖 crate
  
    [clickhouse-rs](https://github.com/suharev7/clickhouse-rs)
    Cargo.toml 配置
  
    ```toml
    [dependencies]
    # clickhouse tcp
    tokio = { version = "1.21.2", features = ["full"] }
    clickhouse-rs = { git = "https://github.com/suharev7/clickhouse-rs", features = ["default"]}
    ```

  * 示例代码
  
    ```rust
    use clickhouse_rs::Pool;

    #[tokio::main]
    async fn main() {
        let database_url="tcp://username:password@service-terrabase-9s29mdlsb7.terrabase-9s2mdsb-hb-public.jvessel2.jdcloud.com:9000?compression=lz4".to_string();
        let pool = Pool::new(database_url);
    
        let mut client = pool.get_handle().await.unwrap();
        let sql = "show databases;";
        let r = client.query(sql).fetch_all().await;
        println!("result is: {:?}", r);
    }

    ```

* http 连接

  * 依赖 crate
    
    [clickhouse.rs](https://github.com/loyd/clickhouse.rs)

    Cargo.toml 配置

    ```toml
    [dependencies]
    # clickhouse http
    clickhouse = {git = "https://github.com/loyd/clickhouse.rs", features = ["test-util"]}
    ```

  * 示例代码

    ```rust
    use clickhouse::Client;
    use clickhouse::Row;
    use serde::{Deserialize, Serialize};
    
    #[derive(Debug, Row, Serialize, Deserialize)]
    struct Database {
        name: String,
    }
    
    #[tokio::main]
    async fn main() {
        let client = Client::default()
        .with_url("https://service-terrabase-9s29mdlsb7.terrabase-9sdlb7-hb-public.jvessel2.jdcloud.com:8123")
        .with_user("username")
        .with_password("password");
    
        let sql = "SHOW databases";
        let r = client.query(sql).fetch_all::<Database>().await;
        println!("result is: {:?}", r);
    }
    ```