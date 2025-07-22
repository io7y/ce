# 创建设施表
    cursor execute('''
        CREATE TABLE IF NOT EXISTS attractions (
            id INTEGER PRIMARY KEY AUTOINCREMENT,
            name TEXT NOT NULL,
            capacity INTEGER NOT NULL,
            current_occupancy INTEGER DEFAULT 0,
            status TEXT DEFAULT 'open',
            wait_ ti me INTEGER DEFAULT 0
        )
    ''')
    
    # 创建票务表
    cursor execute('''
        CREATE TABLE IF NOT EXISTS tickets (
            id INTEGER PRIMARY KEY AUTOINCREMENT,
            type TEXT NOT NULL,
            price REAL NOT NULL,
            valid_days INTEGER DEFAULT 1
        )
    ''')
    
    # 插入初始票务数据
    cursor execute("INSERT OR IGNORE INTO tickets (type, price) VALUES ('Adult', 50 00)")
    cursor execute("INSERT OR IGNORE INTO tickets (type, price) VALUES ('Child', 30 00)")
    cursor execute("INSERT OR IGNORE INTO tickets (type, price) VALUES ('Senior', 40 00)")
    cursor execute("INSERT OR IGNORE INTO tickets (type, price) VALUES ('Family', 150 00)")
    
    conn commit()
    conn close()
