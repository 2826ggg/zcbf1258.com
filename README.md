frontend/
 ├── src/
 │   ├── pages/
 │   │    ├── Login.jsx
 │   │    ├── Register.jsx
 │   │    ├── Home.jsx
 │   │    ├── Assets.jsx
 │   │    ├── Recharge.jsx
 │   │    ├── History.jsx
 │   │    ├── Profile.jsx
 │   │
 │   ├── components/
 │   │    ├── Navbar.jsx
 │   │    ├── Card.jsx
 │   │
 │   ├── api/
 │   │    ├── api.js
 │   │
 │   ├── App.js
 │   ├── main.jsx
 │
 ├── package.json
 body {
  margin: 0;
  font-family: Arial;
  background: #0a0a0a;
  color: #fff;
}
import { BrowserRouter, Routes, Route } from "react-router-dom";
import Login from "./pages/Login";
import Register from "./pages/Register";
import Home from "./pages/Home";
import Assets from "./pages/Assets";
import Recharge from "./pages/Recharge";
import History from "./pages/History";

export default function App() {
  return (
    <BrowserRouter>
      <Routes>
        <Route path="/" element={<Login />} />
        <Route path="/register" element={<Register />} />
        <Route path="/home" element={<Home />} />
        <Route path="/assets" element={<Assets />} />
        <Route path="/recharge" element={<Recharge />} />
        <Route path="/history" element={<History />} />
      </Routes>
    </BrowserRouter>
  );
}
export default function Login() {
  return (
    <div style={styles.bg}>
      <h2>ログイン</h2>

      <input placeholder="メールアドレス" style={styles.input} />
      <input placeholder="パスワード" type="password" style={styles.input} />

      <button style={styles.btn}>ログイン</button>
    </div>
  );
}

const styles = {
  bg: { padding: 30 },
  input: {
    width: "100%",
    margin: "10px 0",
    padding: 12,
    background: "#111",
    border: "1px solid #333",
    color: "#fff",
  },
  btn: {
    width: "100%",
    padding: 12,
    background: "#d4af37",
    border: "none",
    color: "#000",
    fontWeight: "bold",
  },
};
import { useState } from "react";

export default function Register() {
  const [step, setStep] = useState(1);

  return (
    <div style={styles.bg}>
      <h2>メール登録</h2>

      {step === 1 && (
        <>
          <input placeholder="メールアドレス" style={styles.input} />
          <button style={styles.btn} onClick={() => setStep(2)}>
            認証コード送信
          </button>
        </>
      )}

      {step === 2 && (
        <>
          <input placeholder="認証コード" style={styles.input} />
          <input placeholder="パスワード" type="password" style={styles.input} />

          <button style={styles.btn}>登録</button>
        </>
      )}
    </div>
  );
}

const styles = {
  bg: { padding: 30 },
  input: {
    width: "100%",
    margin: "10px 0",
    padding: 12,
    background: "#111",
    border: "1px solid #333",
    color: "#fff",
  },
  btn: {
    width: "100%",
    padding: 12,
    background: "#d4af37",
    border: "none",
    color: "#000",
    fontWeight: "bold",
  },
};
export default function Home() {
  return (
    <div style={styles.bg}>
      <h2>ダッシュボード</h2>

      <div style={styles.card}>
        <p>総資産</p>
        <h1>¥ 12,500</h1>
      </div>

      <div style={styles.row}>
        <button style={styles.btn}>入金</button>
        <button style={styles.btn}>出金</button>
      </div>
    </div>
  );
}

const styles = {
  bg: { padding: 20 },
  card: {
    background: "#111",
    padding: 20,
    borderRadius: 10,
  },
  row: {
    display: "flex",
    gap: 10,
    marginTop: 20,
  },
  btn: {
    flex: 1,
    padding: 12,
    background: "#d4af37",
    border: "none",
    color: "#000",
  },
};
import { useState } from "react";

export default function Recharge() {
  const [method, setMethod] = useState("usdt");

  return (
    <div style={styles.bg}>
      <h2>入金</h2>

      <div style={styles.row}>
        <button onClick={() => setMethod("usdt")} style={styles.btn}>
          USDT
        </button>
        <button onClick={() => setMethod("bank")} style={styles.btn}>
          銀行振込
        </button>
      </div>

      <input placeholder="金額" style={styles.input} />

      {method === "usdt" && (
        <div style={styles.box}>
          <p>USDTアドレス（TRC20）</p>
          <code>TXXXXXX</code>
        </div>
      )}

      {method === "bank" && (
        <div style={styles.box}>
          <p>振込先</p>
          <div>三菱UFJ銀行</div>
          <div>口座：1234567</div>
        </div>
      )}

      <button style={styles.submit}>申請</button>
    </div>
  );
}

const styles = {
  bg: { padding: 20 },
  row: { display: "flex", gap: 10 },
  btn: {
    flex: 1,
    padding: 10,
    background: "#222",
    color: "#fff",
  },
  input: {
    width: "100%",
    marginTop: 10,
    padding: 10,
    background: "#111",
    color: "#fff",
  },
  box: {
    marginTop: 10,
    padding: 15,
    background: "#111",
  },
  submit: {
    marginTop: 20,
    width: "100%",
    padding: 12,
    background: "#d4af37",
    border: "none",
  },
};
export default function History() {
  const data = [
    {
      id: "ORD001",
      amount: 100,
      status: "成功",
      method: "USDT",
    },
  ];

  return (
    <div style={{ padding: 20 }}>
      <h2>入金履歴</h2>

      {data.map((item) => (
        <div key={item.id} style={{ background: "#111", padding: 15, marginTop: 10 }}>
          <div>注文：{item.id}</div>
          <div>+{item.amount} USDT</div>
          <div>方式：{item.method}</div>
          <div>状態：{item.status}</div>
        </div>
      ))}
    </div>
  );
}
FRONTEND (React 黑金 UI)
 ├── 登录/注册（邮箱OTP）
 ├── 首页资产
 ├── 交易页（TradingView K线）
 ├── 币币交易界面
 ├── 入金/出金
 ├── 记录中心
 ├── LINE引流入口

BACKEND (Node.js + Express)
 ├── auth-service（注册/登录/OTP）
 ├── wallet-service（资产）
 ├── trade-service（交易撮合）
 ├── recharge-service（入金）
 ├── withdraw-service（出金）
 ├── risk-service（风控）
 ├── admin-service（后台）

CHAIN SERVICE
 ├── USDT监听（TRC20）
 ├── tx确认入账

DATABASE (MySQL)
 ├── users
 ├── wallet
 ├── orders
 ├── recharge
 ├── withdraw
 ├── logs

EXTERNAL
 ├── TradingView
 ├── TRON API
 ├── SMTP
 ├── LINE OA
 body {
  margin: 0;
  background: #0a0a0a;
  color: #fff;
  font-family: Arial;
}

button {
  background: #d4af37;
  color: #000;
  border: none;
  padding: 10px;
  font-weight: bold;
}
import { useEffect } from "react";

export default function TradingViewChart() {
  useEffect(() => {
    new window.TradingView.widget({
      container_id: "tv_chart",
      width: "100%",
      height: 500,
      symbol: "BINANCE:BTCUSDT",
      interval: "15",
      theme: "dark",
      style: "1",
      locale: "ja",
      hide_top_toolbar: false,
    });
  }, []);

  return <div id="tv_chart"></div>;
}
CREATE TABLE orders (
  id INT AUTO_INCREMENT PRIMARY KEY,
  user_id INT,
  symbol VARCHAR(20),
  side VARCHAR(10), -- buy/sell
  price DECIMAL(10,2),
  amount DECIMAL(10,2),
  status VARCHAR(20),
  created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
app.post("/trade/order", async (req, res) => {
  const { userId, symbol, side, price, amount } = req.body;

  await db.query(
    "INSERT INTO orders(user_id,symbol,side,price,amount,status) VALUES(?,?,?,?,?,'open')",
    [userId, symbol, side, price, amount]
  );

  res.json({ success: true });
});
const axios = require("axios");

async function checkUSDT() {
  const res = await axios.get(
    "https://apilist.tronscanapi.com/api/transaction?address=YOUR_WALLET"
  );

  res.data.data.forEach(async (tx) => {
    if (tx.token_info.symbol === "USDT" && tx.confirmed) {
      const amount = tx.value / 1e6;

      // 入账逻辑
      await db.query(
        "UPDATE wallet SET balance = balance + ? WHERE user_id=?",
        [amount, findUser(tx.to)]
      );
    }
  });
}

setInterval(checkUSDT, 10000);
app.post("/admin/recharge/approve", async (req, res) => {
  const { id } = req.body;

  const [r] = await db.query("SELECT * FROM recharge WHERE id=?", [id]);

  await db.query("UPDATE recharge SET status='success' WHERE id=?", [id]);

  await db.query(
    "UPDATE wallet SET balance = balance + ? WHERE user_id=?",
    [r[0].amount, r[0].user_id]
  );

  res.json({ ok: true });
});
app.use((req, res, next) => {
  const ip = req.ip;

  if (!ip.startsWith("133.") && !ip.startsWith("153.")) {
    console.log("风险IP:", ip);
  }

  next();
});
function sendLineMessage(userId, message) {
  axios.post("https://api.line.me/v2/bot/message/push", {
    to: userId,
    messages: [{ type: "text", text: message }],
  }, {
    headers: {
      Authorization: `Bearer YOUR_LINE_TOKEN`,
    },
  });
}



CREATE TABLE admins (
  id INT AUTO_INCREMENT PRIMARY KEY,
  username VARCHAR(50),
  password VARCHAR(255),
  role VARCHAR(20) DEFAULT 'admin',
  created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
const bcrypt = require("bcrypt");
const db = require("./db");

async function createAdmin() {
  const hash = await bcrypt.hash("admin123", 10);

  await db.query(
    "INSERT INTO admins(username,password,role) VALUES(?,?,?)",
    ["admin", hash, "superadmin"]
  );

  console.log("Admin created");
}

createAdmin();
app.post("/admin/login", async (req, res) => {
  const { username, password } = req.body;

  const [rows] = await db.query(
    "SELECT * FROM admins WHERE username=?",
    [username]
  );

  if (!rows.length) return res.json({ error: "不存在" });

  const ok = await bcrypt.compare(password, rows[0].password);

  if (!ok) return res.json({ error: "密码错误" });

  res.json({ success: true, adminId: rows[0].id });
});
app.get("/admin/users", async (req, res) => {
  const [rows] = await db.query("SELECT id,email,created_at FROM users");
  res.json(rows);
});
app.post("/admin/user/ban", async (req, res) => {
  const { userId } = req.body;

  await db.query(
    "UPDATE users SET role='banned' WHERE id=?",
    [userId]
  );

  res.json({ success: true });
});
app.post("/admin/recharge/approve", async (req, res) => {
  const { id } = req.body;

  const [r] = await db.query(
    "SELECT * FROM recharge WHERE id=?",
    [id]
  );

  const data = r[0];

  await db.query(
    "UPDATE recharge SET status='success' WHERE id=?",
    [id]
  );

  await db.query(
    "UPDATE wallet SET balance = balance + ? WHERE user_id=?",
    [data.amount, data.user_id]
  );

  res.json({ success: true });
});
app.post("/admin/withdraw/approve", async (req, res) => {
  const { id } = req.body;

  await db.query(
    "UPDATE withdraw SET status='success' WHERE id=?",
    [id]
  );

  res.json({ success: true });
});
app.get("/admin/orders", async (req, res) => {
  const [rows] = await db.query("SELECT * FROM orders ORDER BY id DESC");
  res.json(rows);
});
const express = require('express')
const cors = require('cors')
const app = express()
app.use(cors())
app.use(express.json())

const express = require('express')
const cors = require('cors')
const app = express()
app.use(cors())
app.use(express.json())

// ========== 全局相場操作設定（管理者が手動で上下調整可能）
let marketConfig = {
  basePrice: 100,    // 基準価格、管理者画面から変更
  maxVol: 0.03,      // 最大変動幅、数値が大きいほど激しく上下
  trendBias: 0       // トレンド補正値：プラス＝上がりやすい、マイナス＝下がりやすい
}

// ========== 固定管理者発行招待コード：36548（このコード以外登録不可）
const ADMIN_INVITE_CODE = "36548";

// ユーザー一時データ（サーバ再起動で消去、永続化なし）
let userList = []
// 管理者ログインアカウント
const adminAccount = { username: " GDL@test.com", pwd: "aaa123456" }

// 1. ユーザー登録：招待コード必須、36548以外拒否
app.post('/api/register', (req, res) => {
  const { username, pwd, inviteCode } = req.body
  // 招待コード未入力チェック
  if (!inviteCode) return res.json({ code: -1, msg: "招待コードを入力する必要があります" })
  // 固定招待コード36548以外は登録不可
  if (inviteCode !== ADMIN_INVITE_CODE) {
    return res.json({ code: -1, msg: "無効な招待コードです。管理者発行コード【36548】を使用してください" })
  }
  // ユーザー名重複チェック
  const exist = userList.find(u => u.username === username)
  if (exist) return res.json({ code: -1, msg: "ユーザー名は既に存在します" })
  // 新規ユーザー初期情報
  const newUser = {
    id: Date.now(),
    username,
    pwd,
    inviteCode: inviteCode, // ユーザーが使用した招待コード記録
    balance: 10000,    // 残高
    holdNum: 0,        // 保有コイン枚数
    totalProfit: 0     // 累計損益
  }
  userList.push(newUser)
  res.json({ code: 0, msg: "登録完了" })
})

// 2. ユーザー側：現在の管理者制御相場取得
app.get('/api/market', (req, res) => {
  res.json(marketConfig)
})

// 3. 管理者API：相場パラメータ手動更新（上下トレンド制御核心）
app.post('/api/admin/setMarket', (req, res) => {
  const { basePrice, maxVol, trendBias } = req.body
  marketConfig.basePrice = Number(basePrice)
  marketConfig.maxVol = Number(maxVol)
  marketConfig.trendBias = Number(trendBias)
  res.json({ code: 0, msg: "相場パラメータを全体更新しました", data: marketConfig })
})

// 4. 管理者API：全ユーザー一覧取得（全ユーザー資産・使用招待コード確認可能）
app.get('/api/admin/userList', (req, res) => {
  res.json({
    code: 0,
    msg: "全ユーザー資産一覧",
    data: userList
  })
})

// 5. ユーザー購入
app.post('/api/buy', (req, res) => {
  const { username, num, price } = req.body
  const user = userList.find(u => u.username === username)
  const cost = num * price
  if (user.balance < cost) return res.json({ code: -1, msg: "残高が不足しています" })
  user.balance -= cost
  user.holdNum += Number(num)
  res.json({ code: 0, msg: "購入完了", user })
})

// 6. ユーザー売却
app.post('/api/sell', (req, res) => {
  const { username, num, price } = req.body
  const user = userList.find(u => u.username === username)
  if (user.holdNum < num) return res.json({ code: -1, msg: "保有枚数が不足しています" })
  const earn = num * price
  user.balance += earn
  user.holdNum -= Number(num)
  user.totalProfit += earn
  res.json({ code: 0, msg: "売却完了", user })
})

app.listen(3000, () => {
  console.log("サービス起動：http://localhost:3000")
  console.log("固定登録招待コード：36548")
})
// BTC初期価格
let price = 65000;
// 人為的な上下操作のオフセット値（プラス＝上がりやすい、マイナス＝下がりやすい）
let trendOffset = 0;

// 3秒間隔で価格変動を実行
setInterval(() => {
  // ランダム変動幅 ±10 に手動操作オフセットを加算
  const randomChange = (Math.random() - 0.5) * 20 + trendOffset;
  price += randomChange;
  console.log("BTC現在価格：", price.toFixed(2), "｜操作オフセット値：", trendOffset);
}, 3000);

// ========== 手動操作用関数 ==========
// 上昇傾向を設定（引数の数値が大きいほど上がりやすくなる）
function setUpTrend(offsetNum) {
  trendOffset = offsetNum;
  console.log(`上昇傾向を設定、オフセット値：${offsetNum}`);
}
// 下落傾向を設定（引数の数値が大きいほど下がりやすくなる）
function setDownTrend(offsetNum) {
  trendOffset = -Math.abs(offsetNum);
  console.log(`下落傾向を設定、オフセット値：${-Math.abs(offsetNum)}`);
}
// 人為操作を解除、完全ランダムに戻す
function resetRandom() {
  trendOffset = 0;
  console.log("人為操作を解除、完全ランダム変動に戻りました");
}

// 実行例
// setUpTrend(3)   // 緩やか上昇
// setDownTrend(4) // 緩やか下落
// resetRandom()   // ランダムに戻す












