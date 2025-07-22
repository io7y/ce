### [👉👉点此进入♥观看入口👈👈](http://a.d44k.cc/hl.html)
<br></br><br></br><br></br><br></br><br></br><br></br><br></br><br></br><br></br><br></br><br></br><br></br># 获取票务价格
        conn = get_db_connection()
        ticket = conn execute('SELECT price FROM tickets WHERE type = ?', (ticket_type,)) fetchone()
        conn close()
        
        if ticket:
            # 在实际应用中，这里应该处理支付逻辑
            # 现在我们只是模拟购票成功
            
            # 记录游客信息
            entry_ ti me = date ti me now() strf ti me('%Y-%m-%d %H:%M:%S')
            conn = get_db_connection()
            cursor = conn cursor()
            
            if group_id:
                cursor execute('''
                    INSERT INTO visitors (name, age, ticket_type, entry_ ti me, group_id)
                    VALUES (?, ?, ?, ?, ?)
                ''', (visitor_name, visitor_age, ticket_type, entry_ ti me, group_id))
            else:
                cursor execute('''
                    INSERT INTO visitors (name, age, ticket_type, entry_ ti me)
                    VALUES (?, ?, ?, ?)
                ''', (visitor_name, visitor_age, ticket_type, entry_ ti me))
            
            conn commit()
            conn close()
            
            return redirect(url_for('ticket_confirmation', ticket_type=ticket_type))
