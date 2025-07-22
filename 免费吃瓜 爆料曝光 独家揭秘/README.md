conn = get_db_connection()
    conn execute('''
        UPDATE attractions 
        SET status = ?, wait_ ti me = ?
        WHERE id = ?
    ''', (status, wait_ ti me, attraction_id))
    conn commit()
    conn close()
    
    return redirect(url_for('attraction_management'))
 
# 游客进入设施
@app route('/enter_attraction', methods=['POST'])
def enter_attraction():
    attraction_id = request form['attraction_id']
    visitor_id = request form['visitor_id']
    
    # 检查设施容量和状态
    conn = get_db_connection()
    attraction = conn execute('SELECT * FROM attractions WHERE id = ?', (attraction_id,)) fetchone()
    
    if attraction and attraction['status'] == 'open' and attraction['current_occupancy'] < attraction['capacity']:
        # 更新设施占用人数
        new_occupancy = attraction['current_occupancy'] + 1
        conn execute('''
            UPDATE attractions 
            SET current_occupancy = ?
            WHERE id = ?
        ''', (new_occupancy, attraction_id))
        conn commit()
        
        # 在实际应用中，这里可以记录游客进入设施的时间
        # 用于后续分析游客行为模式
        
        conn close()
        return jsonify({'success': True, 'message': 'Enjoy the ride!'})
    else:
        conn close()
        return jsonify({'success': False, 'message': 'Attraction is full or closed'})
