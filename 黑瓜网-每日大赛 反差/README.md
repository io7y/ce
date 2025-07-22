
# app py - 主应用文件
from flask import Flask, render_template, request, redirect, url_for, jsonify
import sqlite3
from date ti me import date ti me
 
app = Flask(__name__)
app secret_key = 'your_secret_key_here'
 
# 数据库初始化
def init_db():
    conn = sqlite3 connect('amusement_park db')
    cursor = conn cursor()
    
    # 创建游客表
    cursor execute('''
        CREATE TABLE IF NOT EXISTS visitors (
            id INTEGER PRIMARY KEY AUTOINCREMENT,
            name TEXT NOT NULL,
            age INTEGER,
            ticket_type TEXT NOT NULL,
            entry_ ti me TEXT NOT NULL,
            exit_ ti me TEXT,
            group_id INTEGER
        )
    ''')
