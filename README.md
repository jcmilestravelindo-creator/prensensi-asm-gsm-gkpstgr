<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no" />
    <title>Presensi ASM-GSM GKPS Tangerang (Online)</title>
    
    <script src="https://cdn.tailwindcss.com"></script>
    <script>
        tailwind.config = {
            theme: {
                extend: {
                    colors: {
                        glass: 'rgba(255, 255, 255, 0.65)',
                        glassBorder: 'rgba(255, 255, 255, 0.6)',
                        primary: '#6366f1', 
                    },
                    fontFamily: {
                        sans: ['Plus Jakarta Sans', 'Inter', 'sans-serif'],
                    },
                    animation: {
                        'blob': 'blob 10s infinite',
                        'float': 'float 6s ease-in-out infinite',
                        'slide-up': 'slideUp 0.5s cubic-bezier(0.16, 1, 0.3, 1)',
                        'pop': 'pop 0.3s cubic-bezier(0.175, 0.885, 0.32, 1.275)',
                    },
                    keyframes: {
                        blob: {
                            '0%': { transform: 'translate(0px, 0px) scale(1)' },
                            '33%': { transform: 'translate(30px, -50px) scale(1.1)' },
                            '66%': { transform: 'translate(-20px, 20px) scale(0.9)' },
                            '100%': { transform: 'translate(0px, 0px) scale(1)' },
                        },
                        float: {
                            '0%, 100%': { transform: 'translateY(0)' },
                            '50%': { transform: 'translateY(-10px)' },
                        },
                        slideUp: {
                            'from': { opacity: 0, transform: 'translateY(40px)' },
                            'to': { opacity: 1, transform: 'translateY(0)' },
                        },
                        pop: {
                            '0%': { transform: 'scale(0.9)', opacity: 0 },
                            '100%': { transform: 'scale(1)', opacity: 1 },
                        }
                    }
                }
            }
        }
    </script>
    
    <script src="https://unpkg.com/html5-qrcode" type="text/javascript"></script>
    
    <script src="https://cdn.sheetjs.com/xlsx-0.19.3/package/dist/xlsx.full.min.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/jspdf/2.5.1/jspdf.umd.min.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/jspdf-autotable/3.8.1/jspdf.plugin.autotable.min.js"></script>

    <script src="https://unpkg.com/@babel/standalone/babel.min.js"></script>

    <style>
        @import url('https://fonts.googleapis.com/css2?family=Plus+Jakarta+Sans:wght@400;500;600;700;800&display=swap');
        ::-webkit-scrollbar { width: 0px; background: transparent; }
        
        body { 
            overscroll-behavior-y: none;
            background-color: #f0f2f5; 
            font-family: 'Plus Jakarta Sans', sans-serif;
            -webkit-tap-highlight-color: transparent;
        }

        .glass-panel {
            background: rgba(255, 255, 255, 0.7);
            backdrop-filter: blur(20px);
            -webkit-backdrop-filter: blur(20px);
            border: 1px solid rgba(255, 255, 255, 0.6);
            box-shadow: 0 8px 32px 0 rgba(31, 38, 135, 0.1);
        }

        .glass-card {
            background: rgba(255, 255, 255, 0.85);
            backdrop-filter: blur(12px);
            border: 1px solid rgba(255, 255, 255, 0.8);
            box-shadow: 0 4px 20px rgba(0, 0, 0, 0.05);
        }

        .glass-nav {
            background: rgba(255, 255, 255, 0.8);
            backdrop-filter: blur(25px);
            -webkit-backdrop-filter: blur(25px);
            border-top: 1px solid rgba(255, 255, 255, 0.5);
            box-shadow: 0 -4px 30px rgba(0, 0, 0, 0.05);
        }

        @keyframes scan-line {
            0% { top: 10%; opacity: 0; }
            50% { opacity: 1; }
            100% { top: 90%; opacity: 0; }
        }
        .animate-scan { animation: scan-line 2.5s ease-in-out infinite; }

        #reader video { 
            object-fit: cover;
            border-radius: 1.5rem; 
            width: 100% !important;
            height: 100% !important;
        }

        .loader {
            border: 4px solid #f3f3f3;
            border-top: 4px solid #6366f1;
            border-radius: 50%;
            width: 40px;
            height: 40px;
            animation: spin 1s linear infinite;
        }
        @keyframes spin { 0% { transform: rotate(0deg); } 100% { transform: rotate(360deg); } }
        
        .pb-safe { padding-bottom: env(safe-area-inset-bottom, 24px); }
        .no-scrollbar::-webkit-scrollbar { display: none; }
        .no-scrollbar { -ms-overflow-style: none; scrollbar-width: none; }
    </style>

    <script type="importmap">
    {
        "imports": {
            "react": "https://esm.sh/react@18.2.0",
            "react-dom/client": "https://esm.sh/react-dom@18.2.0/client?deps=react@18.2.0",
            "react-dom": "https://esm.sh/react-dom@18.2.0?deps=react@18.2.0",
            "react-router-dom": "https://esm.sh/react-router-dom@6.22.0?deps=react@18.2.0,react-dom@18.2.0",
            "lucide-react": "https://esm.sh/lucide-react@0.344.0?deps=react@18.2.0",
            "recharts": "https://esm.sh/recharts@2.12.0?deps=react@18.2.0,react-dom@18.2.0",
            "react-qr-code": "https://esm.sh/react-qr-code@2.0.12?deps=react@18.2.0",
            "firebase/app": "https://www.gstatic.com/firebasejs/10.8.0/firebase-app.js",
            "firebase/auth": "https://www.gstatic.com/firebasejs/10.8.0/firebase-auth.js",
            "firebase/firestore": "https://www.gstatic.com/firebasejs/10.8.0/firebase-firestore.js",
            "firebase/analytics": "https://www.gstatic.com/firebasejs/10.8.0/firebase-analytics.js"
        }
    }
    </script>
</head>
<body>
    <div id="root"></div>

    <script type="text/babel" data-type="module">
        import React, { useState, useEffect, useRef, useMemo } from 'react';
        import { createRoot } from 'react-dom/client';
        import { HashRouter, Routes, Route, useNavigate, useLocation } from 'react-router-dom';
        import { 
            LayoutDashboard, QrCode, Users, BarChart3, LogOut, Church, CreditCard,
            CheckCircle, AlertCircle, Camera, Trash2, Download, Search, Upload,
            ChevronRight, Calendar, User, ShieldCheck, Sparkles, Zap, Plus, X, RefreshCw, BookOpen, PenTool,
            Bell, Activity, MessageSquare, Send, Radio, TrendingUp, Briefcase, GraduationCap, Clock, FileText, CalendarDays, MapPin, Edit, BrainCircuit, Cloud, CloudOff, FileSpreadsheet, File, Lock, Key, Power, Eye, Timer
        } from 'lucide-react';
        import { BarChart, Bar, ResponsiveContainer, PieChart, Pie, Cell, Tooltip, XAxis, YAxis, CartesianGrid } from 'recharts';
        import QRCode from 'react-qr-code';
        
        // --- FIREBASE INTEGRATION ---
        import { initializeApp } from "firebase/app";
        import { getAnalytics } from "firebase/analytics";
        import { getAuth, signInAnonymously, signInWithCustomToken } from "firebase/auth";
        import { getFirestore, collection, getDocs, setDoc, doc, addDoc, updateDoc, deleteDoc, onSnapshot } from "firebase/firestore";

        // CONFIGURATION HANDLING
        // Cobalah menggunakan config environment jika tersedia (untuk preview),
        // jika tidak, gunakan config hardcoded milik user.
        let firebaseConfig;
        try {
            firebaseConfig = JSON.parse(__firebase_config);
        } catch (e) {
            // Fallback ke config user jika variabel environment tidak ada
            firebaseConfig = {
                apiKey: "AIzaSyDDtjCJO09qP3kwOcoctObU-qOg-GTnrTE",
                authDomain: "sundayschoolattendance-58661.firebaseapp.com",
                databaseURL: "https://sundayschoolattendance-58661-default-rtdb.asia-southeast1.firebasedatabase.app",
                projectId: "sundayschoolattendance-58661",
                storageBucket: "sundayschoolattendance-58661.firebasestorage.app",
                messagingSenderId: "1055300658311",
                appId: "1:1055300658311:web:2db2708b0c8bfa5aa54422",
                measurementId: "G-PCB8J7RRHJ"
            };
        }

        const app = initializeApp(firebaseConfig);
        const analytics = getAnalytics(app);
        const auth = getAuth(app); 
        const db = getFirestore(app);
        
        // --- APP ID FOR PATHING ---
        // PENTING: Gunakan App ID ini untuk path Firestore agar tidak kena error "Missing permissions"
        const appId = typeof __app_id !== 'undefined' ? __app_id : 'default-app-id';

        // Helper untuk mendapatkan referensi koleksi di path yang benar
        const getCollectionRef = (colName) => {
            return collection(db, 'artifacts', appId, 'public', 'data', colName);
        };

        // Helper untuk mendapatkan referensi dokumen di path yang benar
        const getDocRef = (colName, docId) => {
            return doc(db, 'artifacts', appId, 'public', 'data', colName, String(docId));
        };

        // --- TIMEZONE FIX HELPER (CRITICAL FOR ATTENDANCE) ---
        // Memaksa waktu server/aplikasi mengikuti Waktu Indonesia Barat (GMT+7)
        // Apapun settingan jam di HP user, data yang masuk akan tetap dianggap tanggal WIB.
        const getLocalDate = () => {
            const now = new Date();
            // Konversi waktu saat ini ke UTC Timestamp
            const utc = now.getTime() + (now.getTimezoneOffset() * 60000);
            // Tambahkan offset 7 Jam (WIB) secara manual
            const wibTime = new Date(utc + (7 * 3600000));
            
            const year = wibTime.getFullYear();
            const month = String(wibTime.getMonth() + 1).padStart(2, '0');
            const day = String(wibTime.getDate()).padStart(2, '0');
            return `${year}-${month}-${day}`;
        };

        // --- FIREBASE HELPERS ---
        const syncFromFirestore = async () => {
            if (!auth.currentUser) return false; // Jangan sync jika offline
            
            const collections = [
                { name: 'users', key: 'gkps_users_v3' },
                { name: 'attendance', key: 'gkps_att_v3' },
                { name: 'schedules', key: 'gkps_sched_v3' },
                { name: 'materials', key: 'gkps_mat_v3' },
                { name: 'activities', key: 'gkps_act_v3' },
                { name: 'notifications', key: 'gkps_notif_v3' }
            ];
            let hasData = false;
            try {
                for (const col of collections) {
                    const querySnapshot = await getDocs(getCollectionRef(col.name));
                    const data = [];
                    querySnapshot.forEach((doc) => {
                        data.push(doc.data());
                    });
                    if (data.length > 0) {
                        localStorage.setItem(col.key, JSON.stringify(data));
                        hasData = true;
                    }
                }
                console.log("Sync complete from Firestore");
            } catch (e) {
                console.error("Gagal sinkronisasi data:", e);
            }
            return hasData;
        };

        const pushToFirestore = async (collectionName, data, id) => {
            try {
                // Pastikan user terautentikasi sebelum menulis
                if (auth.currentUser) {
                    await setDoc(getDocRef(collectionName, id), data);
                    console.log(`Berhasil simpan ke ${collectionName}:`, id);
                } else {
                    console.warn("Offline: Data disimpan lokal saja.");
                }
            } catch (e) {
                console.error(`Gagal push ke Firestore (${collectionName}):`, e);
            }
        };

        const deleteFromFirestore = async (collectionName, id) => {
            try {
                if (auth.currentUser) {
                    await deleteDoc(getDocRef(collectionName, id));
                }
            } catch (e) {
                console.error("Gagal hapus di Firestore:", e);
            }
        }

        // --- DATA & CONFIG ---
        const MOCK_VERSES = [
            "Amsal 1:7 - Takut akan TUHAN adalah permulaan pengetahuan.",
            "Filipi 4:13 - Segala perkara dapat kutanggung di dalam Dia.",
            "Yosua 1:9 - Bukankah telah Kuperintahkan kepadamu: kuatkan dan teguhkanlah hatimu?",
            "Yeremia 29:11 - Sebab Aku ini mengetahui rancangan-rancangan apa yang ada pada-Ku mengenai kamu."
        ];
        
        const ML_HEROES = [
            "Alucard", "Miya", "Layla", "Zilong", "Tigreal", "Nana", "Eudora", "Gord",
            "Saber", "Balmond", "Akai", "Franco", "Chou", "Gusion", "Fanny", "Lesley"
        ];

        const JACOB_SONS = [
            "Ruben", "Simeon", "Lewi", "Yehuda", "Dan", "Naftali", 
            "Gad", "Asyer", "Isakhar", "Zebulon", "Yusuf", "Benyamin"
        ];

        const UserRole = { ADMIN: 'ADMIN', TEACHER: 'TEACHER', STUDENT: 'STUDENT' };
        const STORAGE = { 
            USERS: 'gkps_users_v3', 
            ATTENDANCE: 'gkps_att_v3', 
            CLASSES: 'gkps_cls_v3', 
            SESSION: 'gkps_sess_v3', 
            MATERIALS: 'gkps_mat_v3',
            ACTIVITIES: 'gkps_act_v3', 
            NOTIFICATIONS: 'gkps_notif_v3', 
            SCHEDULES: 'gkps_sched_v3' 
        };
        
        const DEFAULT_USERS = [
            { id: '1', name: 'Admin Utama', role: 'ADMIN', qrCode: 'ADMIN-001', gender: 'Laki-Laki', pin: 'admin123', isActive: true, lastLogin: new Date().toISOString() },
            { id: '2', name: 'Guru Sekolah Minggu', role: 'TEACHER', className: 'Kelas Daud', qrCode: 'GURU-001', gender: 'Perempuan', pin: '123456', isActive: true },
            { id: '3', name: 'Timothy Simanjuntak', role: 'STUDENT', className: 'Kelas Daud', qrCode: 'S-001', gender: 'Laki-Laki', pin: '123456', isActive: true },
            { id: '4', name: 'Sarah Damanik', role: 'STUDENT', className: 'Kelas Ester', qrCode: 'S-002', gender: 'Perempuan', pin: '123456', isActive: true },
        ];
        const DEFAULT_CLASSES = [
            { id: 'c1', name: 'Kelas Daud', desc: '4-6 Tahun' },
            { id: 'c2', name: 'Kelas Daniel', desc: '7-9 Tahun' },
            { id: 'c3', name: 'Kelas Paulus', desc: '10-12 Tahun' },
            { id: 'c4', name: 'Kelas Ester', desc: '13+ Tahun' }
        ];
        const DEFAULT_SCHEDULES = [
            { id: 's1', className: 'Kelas Daud', date: getLocalDate(), time: '08:00 - 09:30', activity: 'Ibadah Minggu', theme: 'Tuhan Yesus Baik', speaker: 'Kak Lisa', location: 'R. Daud Lt. 1', status: 'upcoming' },
            { id: 's2', className: 'Kelas Daniel', date: getLocalDate(), time: '08:00 - 09:30', activity: 'Ibadah & Aktivitas', theme: 'Daud Melawan Goliat', speaker: 'Kak Budi', location: 'R. Daniel Lt. 1', status: 'upcoming' },
        ];

        // --- GEMINI AI SERVICE ---
        const GeminiService = {
            call: async (prompt) => {
                const apiKey = ""; // API Key
                const url = `https://generativelanguage.googleapis.com/v1beta/models/gemini-2.5-flash-preview-09-2025:generateContent?key=${apiKey}`;
                const payload = {
                    contents: [{ parts: [{ text: prompt }] }],
                    generationConfig: { responseMimeType: "application/json" }
                };

                const delays = [1000, 2000, 4000];
                for (let i = 0; i <= 3; i++) {
                    try {
                        const response = await fetch(url, {
                            method: 'POST',
                            headers: { 'Content-Type': 'application/json' },
                            body: JSON.stringify(payload)
                        });
                        if (!response.ok) throw new Error(`HTTP error! status: ${response.status}`);
                        
                        const data = await response.json();
                        const text = data.candidates?.[0]?.content?.parts?.[0]?.text;
                        return JSON.parse(text);
                    } catch (error) {
                        if (i === 3) throw error;
                        await new Promise(resolve => setTimeout(resolve, delays[i]));
                    }
                }
            }
        };

        // --- SERVICES (MODIFIED FOR FIREBASE) ---
        const DB = {
            get: (key, def) => {
                try { return JSON.parse(localStorage.getItem(key)) || def; } catch { return def; }
            },
            set: (key, val) => localStorage.setItem(key, JSON.stringify(val)),
            users: {
                update: (updatedUser) => {
                    const users = DB.get(STORAGE.USERS, DEFAULT_USERS);
                    const index = users.findIndex(u => u.id === updatedUser.id);
                    if (index !== -1) {
                        users[index] = updatedUser;
                        DB.set(STORAGE.USERS, users);
                        pushToFirestore('users', updatedUser, updatedUser.id);
                        return true;
                    }
                    users.push(updatedUser);
                    DB.set(STORAGE.USERS, users);
                    pushToFirestore('users', updatedUser, updatedUser.id);
                    return true;
                },
                add: (newUser) => {
                    const users = DB.get(STORAGE.USERS, DEFAULT_USERS);
                    users.push(newUser);
                    DB.set(STORAGE.USERS, users);
                    pushToFirestore('users', newUser, newUser.id);
                },
                delete: (id) => {
                    const users = DB.get(STORAGE.USERS, DEFAULT_USERS);
                    const updated = users.filter(u => u.id !== id);
                    DB.set(STORAGE.USERS, updated);
                    deleteFromFirestore('users', id);
                }
            },
            att: {
                add: (record) => {
                    const all = DB.get(STORAGE.ATTENDANCE, []);
                    // Check duplicate strictly on user ID and DATE string
                    if (all.some(r => r.userId === record.userId && r.date === record.date)) return false;
                    DB.set(STORAGE.ATTENDANCE, [...all, record]);
                    pushToFirestore('attendance', record, record.id);
                    return true;
                }
            },
            materials: {
                getLatest: (className) => {
                    const all = DB.get(STORAGE.MATERIALS, []);
                    const classMaterials = all.filter(m => m.className === className);
                    return classMaterials.sort((a,b) => new Date(b.createdAt) - new Date(a.createdAt))[0];
                },
                save: (material) => {
                    const all = DB.get(STORAGE.MATERIALS, []);
                    DB.set(STORAGE.MATERIALS, [material, ...all]);
                    pushToFirestore('materials', material, material.id);
                }
            },
            activities: {
                add: (userName, action) => {
                    const all = DB.get(STORAGE.ACTIVITIES, []);
                    const newLog = { id: Date.now(), userName, action, timestamp: new Date().toISOString() };
                    DB.set(STORAGE.ACTIVITIES, [newLog, ...all].slice(0, 50));
                    pushToFirestore('activities', newLog, newLog.id);
                },
                get: () => DB.get(STORAGE.ACTIVITIES, [])
            },
            notifications: {
                broadcast: (title, message, sender, scheduledTime = null) => {
                    const all = DB.get(STORAGE.NOTIFICATIONS, []);
                    const newNotif = { 
                        id: Date.now(), 
                        title, 
                        message, 
                        sender, 
                        timestamp: new Date().toISOString(),
                        scheduledTime: scheduledTime ? scheduledTime : new Date().toISOString(),
                        status: scheduledTime && new Date(scheduledTime) > new Date() ? 'scheduled' : 'sent'
                    };
                    DB.set(STORAGE.NOTIFICATIONS, [newNotif, ...all]);
                    pushToFirestore('notifications', newNotif, newNotif.id);
                },
                get: () => DB.get(STORAGE.NOTIFICATIONS, [])
            },
            schedules: {
                get: (className) => {
                    const all = DB.get(STORAGE.SCHEDULES, DEFAULT_SCHEDULES);
                    if (!className || className === 'ALL') return all;
                    return all.filter(s => s.className === className);
                },
                add: (sched) => {
                    const all = DB.get(STORAGE.SCHEDULES, DEFAULT_SCHEDULES);
                    DB.set(STORAGE.SCHEDULES, [sched, ...all]);
                    pushToFirestore('schedules', sched, sched.id);
                },
                update: (updatedSched) => {
                    const all = DB.get(STORAGE.SCHEDULES, DEFAULT_SCHEDULES);
                    const index = all.findIndex(s => s.id === updatedSched.id);
                    if (index !== -1) {
                        all[index] = updatedSched;
                        DB.set(STORAGE.SCHEDULES, all);
                        pushToFirestore('schedules', updatedSched, updatedSched.id);
                        return true;
                    }
                    return false;
                },
                delete: (id) => {
                    const all = DB.get(STORAGE.SCHEDULES, DEFAULT_SCHEDULES);
                    DB.set(STORAGE.SCHEDULES, all.filter(s => s.id !== id));
                    deleteFromFirestore('schedules', id);
                }
            }
        };

        // --- HELPER ---
        const formatDateIndo = (dateStr) => {
            const date = new Date(dateStr);
            return date.toLocaleDateString('id-ID', { weekday: 'long', day: 'numeric', month: 'long', year: 'numeric' });
        };
        
        const isNotifVisible = (n) => {
             if (!n.scheduledTime) return true;
             return new Date(n.scheduledTime) <= new Date();
        };

        // --- UI COMPONENTS ---
        const Background = () => (
            <div className="fixed inset-0 overflow-hidden pointer-events-none -z-10 bg-[#f3f4f6]">
                <div className="absolute top-0 left-0 w-full h-full bg-gradient-to-br from-indigo-50/50 via-purple-50/50 to-pink-50/50"></div>
                <div className="absolute top-[-10%] left-[-10%] w-96 h-96 bg-purple-300 rounded-full mix-blend-multiply filter blur-3xl opacity-30 animate-blob"></div>
                <div className="absolute top-[-10%] right-[-10%] w-96 h-96 bg-yellow-200 rounded-full mix-blend-multiply filter blur-3xl opacity-30 animate-blob animation-delay-2000"></div>
                <div className="absolute -bottom-32 left-20 w-96 h-96 bg-pink-300 rounded-full mix-blend-multiply filter blur-3xl opacity-30 animate-blob animation-delay-4000"></div>
            </div>
        );

        const Button = ({ children, onClick, variant = 'primary', className = '' }) => {
            const styles = {
                primary: "bg-gradient-to-r from-indigo-600 to-pink-500 text-white shadow-lg shadow-indigo-500/30 border-0",
                secondary: "bg-white text-slate-700 border border-slate-200 hover:bg-slate-50",
                glass: "bg-white/40 backdrop-blur-md border border-white/60 text-indigo-700 hover:bg-white/60",
                danger: "bg-red-50 text-red-600 border border-red-100 hover:bg-red-100"
            };
            return (
                <button onClick={onClick} className={`w-full py-4 rounded-2xl font-bold transition-all active:scale-95 flex items-center justify-center gap-2 ${styles[variant]} ${className}`}>
                    {children}
                </button>
            );
        };

        const Avatar = ({ name, seed, style = 'avataaars', size = 'md', className='', onClick }) => {
            const s = size === 'lg' ? 'w-16 h-16 text-2xl' : size === 'xl' ? 'w-24 h-24 text-4xl' : 'w-10 h-10 text-sm';
            const avatarSeed = seed || name;
            const src = `https://api.dicebear.com/7.x/${style}/svg?seed=${avatarSeed}&backgroundColor=transparent`;
            return (
                <div onClick={onClick} className={`${s} rounded-full bg-gradient-to-tr from-indigo-400 to-pink-400 p-0.5 shadow-lg ${className} ${onClick ? 'cursor-pointer hover:scale-105 transition-transform' : ''}`}>
                    <div className="w-full h-full bg-white rounded-full flex items-center justify-center overflow-hidden">
                        <img 
                            src={src} 
                            alt={name} 
                            className="w-full h-full object-cover"
                            onError={(e) => {e.target.src = `https://api.dicebear.com/7.x/initials/svg?seed=${name}`}}
                        />
                    </div>
                </div>
            );
        };

        const LoadingScreen = () => (
            <div className="min-h-screen flex flex-col items-center justify-center bg-slate-50 relative overflow-hidden">
                <Background />
                <div className="glass-panel p-8 rounded-3xl flex flex-col items-center gap-4 animate-pop">
                    <div className="loader"></div>
                    <p className="text-slate-600 font-bold text-sm">Menghubungkan Database...</p>
                </div>
            </div>
        );

        // --- MODALS & SCREENS ---
        const ScheduleManagerModal = ({ user, onClose }) => {
            const [schedules, setSchedules] = useState([]);
            const [form, setForm] = useState({
                className: user.role === 'TEACHER' ? user.className : DEFAULT_CLASSES[0].name,
                date: getLocalDate(), // FIX: Use local date 
                time: '', activity: '', theme: '', speaker: '', location: ''
            });
            const [filterClass, setFilterClass] = useState(user.role === 'TEACHER' ? user.className : 'ALL');
            const [confirmId, setConfirmId] = useState(null);
            const [editingId, setEditingId] = useState(null);

            useEffect(() => {
                const data = DB.schedules.get(filterClass);
                data.sort((a, b) => new Date(b.date) - new Date(a.date));
                setSchedules(data);
            }, [filterClass]);

            const handleSubmit = () => {
                if(!form.activity || !form.time || !form.date) return alert("Mohon lengkapi tanggal, aktivitas dan waktu");
                if (editingId) {
                    const updatedSched = { ...form, id: editingId, status: 'upcoming' };
                    DB.schedules.update(updatedSched);
                    DB.activities.add(user.name, `Mengubah jadwal: ${form.activity}`);
                    alert("Jadwal berhasil diperbarui!");
                    setEditingId(null);
                } else {
                    const newSched = { ...form, id: Date.now().toString(), status: 'upcoming' };
                    DB.schedules.add(newSched);
                    DB.activities.add(user.name, `Membuat jadwal: ${form.activity}`);
                    alert("Jadwal ditambahkan!");
                }
                
                const data = DB.schedules.get(filterClass);
                data.sort((a, b) => new Date(b.date) - new Date(a.date));
                setSchedules(data);
                
                setForm({
                    className: user.role === 'TEACHER' ? user.className : DEFAULT_CLASSES[0].name,
                    date: getLocalDate(), // FIX: Use local date
                    time: '', activity: '', theme: '', speaker: '', location: ''
                }); 
            };

            const handleEdit = (sched) => {
                setForm(sched);
                setEditingId(sched.id);
            };

            const handleCancelEdit = () => {
                setEditingId(null);
                setForm({
                    className: user.role === 'TEACHER' ? user.className : DEFAULT_CLASSES[0].name,
                    date: getLocalDate(), 
                    time: '', activity: '', theme: '', speaker: '', location: ''
                });
            };

            const handleDelete = (id, activityName) => {
                DB.schedules.delete(id);
                DB.activities.add(user.name, `Menghapus jadwal: ${activityName}`);
                const data = DB.schedules.get(filterClass);
                data.sort((a, b) => new Date(b.date) - new Date(a.date));
                setSchedules(data);
                setConfirmId(null);
                if (editingId === id) handleCancelEdit();
            };

            return (
                <div className="fixed inset-0 z-[60] flex items-center justify-center p-4">
                    <div className="absolute inset-0 bg-black/20 backdrop-blur-sm" onClick={onClose}></div>
                    <div className="bg-white rounded-[2rem] p-6 w-full max-w-md relative z-10 shadow-2xl animate-pop h-[80vh] flex flex-col">
                        <div className="flex justify-between items-center mb-4">
                            <h3 className="text-xl font-bold text-slate-800 flex items-center gap-2"><CalendarDays size={20} className="text-indigo-500"/> {editingId ? 'Edit Jadwal' : 'Kelola Jadwal'}</h3>
                            <button onClick={onClose}><X size={20} className="text-slate-400 hover:text-slate-600"/></button>
                        </div>

                        <div className="space-y-3 mb-6 bg-slate-50 p-4 rounded-2xl border border-slate-100 relative">
                            {editingId && <div className="absolute top-0 right-0 bg-amber-100 text-amber-600 text-[10px] font-bold px-2 py-1 rounded-bl-xl rounded-tr-xl">Mode Edit</div>}
                            
                            {user.role === 'ADMIN' && (
                                <select value={form.className} onChange={e=>setForm({...form, className: e.target.value})} className="w-full p-2 rounded-xl border text-sm font-semibold text-slate-600">
                                    {DEFAULT_CLASSES.map(c => <option key={c.id} value={c.name}>{c.name}</option>)}
                                </select>
                            )}
                            
                            <div className="grid grid-cols-2 gap-2">
                                <input type="date" value={form.date} onChange={e=>setForm({...form, date: e.target.value})} className="p-2 rounded-xl border text-sm text-slate-600 font-semibold"/>
                                <input value={form.time} onChange={e=>setForm({...form, time: e.target.value})} placeholder="Jam (08:00 - 10:00)" className="p-2 rounded-xl border text-sm"/>
                            </div>
                            <input value={form.activity} onChange={e=>setForm({...form, activity: e.target.value})} placeholder="Nama Kegiatan" className="w-full p-2 rounded-xl border text-sm"/>
                            <input value={form.theme} onChange={e=>setForm({...form, theme: e.target.value})} placeholder="Tema (Opsional)" className="w-full p-2 rounded-xl border text-sm"/>
                            <div className="grid grid-cols-2 gap-2">
                                <input value={form.speaker} onChange={e=>setForm({...form, speaker: e.target.value})} placeholder="Pengajar" className="p-2 rounded-xl border text-sm"/>
                                <input value={form.location} onChange={e=>setForm({...form, location: e.target.value})} placeholder="Lokasi" className="p-2 rounded-xl border text-sm"/>
                            </div>
                            
                            <div className="flex gap-2">
                                <Button onClick={handleSubmit} className="py-2 text-sm flex-1">{editingId ? 'Simpan Perubahan' : 'Tambah Jadwal'}</Button>
                                {editingId && <Button onClick={handleCancelEdit} variant="secondary" className="py-2 text-sm w-1/3">Batal</Button>}
                            </div>
                        </div>

                        {user.role === 'ADMIN' && (
                            <div className="mb-4">
                                <select value={filterClass} onChange={e=>setFilterClass(e.target.value)} className="w-full p-2 rounded-xl border bg-white text-sm font-bold text-slate-600">
                                    <option value="ALL">Semua Kelas</option>
                                    {DEFAULT_CLASSES.map(c => <option key={c.id} value={c.name}>{c.name}</option>)}
                                </select>
                            </div>
                        )}

                        <div className="flex-1 overflow-y-auto space-y-3 pb-4">
                            {schedules.length === 0 ? <p className="text-center text-slate-400 text-sm mt-4">Belum ada jadwal.</p> : schedules.map(s => (
                                <div key={s.id} className={`p-3 border rounded-xl flex justify-between items-start bg-white shadow-sm transition-colors ${editingId === s.id ? 'border-indigo-500 ring-2 ring-indigo-100' : 'border-slate-100 hover:border-indigo-200'}`}>
                                    <div className="flex-1">
                                        <p className="text-[10px] font-bold text-indigo-500 bg-indigo-50 px-2 py-0.5 rounded w-fit mb-1">{s.className}</p>
                                        <h4 className="font-bold text-slate-800 text-sm">{s.activity}</h4>
                                        <p className="text-xs text-slate-500 flex items-center gap-1 mt-1">
                                            <Calendar size={10}/> {formatDateIndo(s.date)} • {s.time}
                                        </p>
                                    </div>
                                    <div className="flex flex-col gap-1 ml-2">
                                        <button onClick={()=>handleEdit(s)} className="p-2 bg-slate-50 text-slate-400 rounded-lg hover:bg-blue-50 hover:text-blue-500 transition-all" title="Edit Jadwal"><Edit size={16}/></button>
                                        {confirmId === s.id ? (
                                            <div className="flex flex-col gap-1 mt-1">
                                                <button onClick={()=>handleDelete(s.id, s.activity)} className="px-2 py-1 bg-red-500 text-white text-[10px] font-bold rounded hover:bg-red-600">Hapus!</button>
                                                <button onClick={()=>setConfirmId(null)} className="px-2 py-1 bg-slate-200 text-slate-600 text-[10px] font-bold rounded hover:bg-slate-300">Batal</button>
                                            </div>
                                        ) : (
                                            <button onClick={()=>setConfirmId(s.id)} className="p-2 bg-slate-50 text-slate-400 rounded-lg hover:bg-red-50 hover:text-red-500 transition-all" title="Hapus Jadwal"><Trash2 size={16}/></button>
                                        )}
                                    </div>
                                </div>
                            ))}
                        </div>
                    </div>
                </div>
            );
        };

        const NotificationModal = ({ onClose }) => {
            const [notifs, setNotifs] = useState([]);
            useEffect(() => {
                const all = DB.notifications.get();
                const visible = all.filter(n => isNotifVisible(n));
                setNotifs(visible);
            }, []);

            return (
                <div className="fixed inset-0 z-[70] flex items-center justify-center p-4">
                    <div className="absolute inset-0 bg-black/20 backdrop-blur-sm" onClick={onClose}></div>
                    <div className="bg-white rounded-[2rem] p-6 w-full max-w-sm relative z-10 shadow-2xl animate-pop h-[60vh] flex flex-col">
                        <div className="flex justify-between items-center mb-4">
                            <h3 className="text-xl font-bold text-slate-800 flex items-center gap-2"><Bell size={20} className="text-indigo-500"/> Notifikasi</h3>
                            <button onClick={onClose}><X size={20} className="text-slate-400 hover:text-slate-600"/></button>
                        </div>
                        <div className="flex-1 overflow-y-auto space-y-3">
                            {notifs.length === 0 ? (
                                <p className="text-center text-slate-400 mt-10 text-sm">Belum ada pengumuman.</p>
                            ) : (
                                notifs.map(n => (
                                    <div key={n.id} className="p-3 bg-indigo-50 border border-indigo-100 rounded-xl">
                                        <div className="flex justify-between items-start mb-1">
                                            <h4 className="font-bold text-indigo-900 text-sm">{n.title}</h4>
                                            <span className="text-[10px] text-indigo-400">{new Date(n.timestamp).toLocaleDateString()}</span>
                                        </div>
                                        <p className="text-slate-600 text-xs leading-relaxed">{n.message}</p>
                                        <p className="text-[10px] text-indigo-400 mt-2 font-medium">Oleh: {n.sender}</p>
                                    </div>
                                ))
                            )}
                        </div>
                    </div>
                </div>
            );
        };

        const ProfileModal = ({ user, onClose, onUpdate }) => {
            const [seed, setSeed] = useState(user.avatarSeed || user.name);
            const [style, setStyle] = useState(user.avatarStyle || 'avataaars'); 
            const [collection, setCollection] = useState('random'); 
            const [newPin, setNewPin] = useState(user.pin || '123456');

            const handleSave = () => { 
                if (!newPin) return alert("PIN tidak boleh kosong!");
                if (newPin.length !== 6 || isNaN(newPin)) return alert("PIN harus 6 digit angka!");
                onUpdate({ ...user, avatarSeed: seed, avatarStyle: style, pin: newPin });
                alert("Profil diperbarui!");
                onClose(); 
            };

            const selectPreset = (name, presetStyle) => {
                setSeed(name);
                setStyle(presetStyle);
            };

            return (
                <div className="fixed inset-0 z-[60] flex items-center justify-center p-4">
                    <div className="absolute inset-0 bg-black/20 backdrop-blur-sm" onClick={onClose}></div>
                    <div className="bg-white rounded-[2rem] p-6 w-full max-w-sm relative z-10 shadow-2xl animate-pop max-h-[85vh] flex flex-col">
                        <button onClick={onClose} className="absolute top-4 right-4 text-slate-400 hover:text-slate-600"><X size={24} /></button>
                        
                        <div className="text-center mb-4">
                            <h3 className="text-xl font-bold text-slate-800">Edit Profil</h3>
                            <p className="text-slate-500 text-sm">Pilih avatar favoritmu</p>
                        </div>

                        <div className="flex justify-center mb-6">
                            <div className="flex flex-col items-center">
                                <Avatar name={user.name} seed={seed} style={style} size="xl" className="border-4 border-white shadow-xl mb-2" />
                                <div className="bg-white p-2 rounded-xl shadow-inner border border-slate-100">
                                    <QRCode value={user.qrCode || user.id} size={80} />
                                </div>
                                <p className="text-[10px] text-slate-400 mt-1 font-mono">{user.qrCode}</p>
                            </div>
                        </div>

                        <div className="flex-1 overflow-y-auto pr-1">
                            <div className="flex gap-2 mb-4 overflow-x-auto pb-2 no-scrollbar">
                                <button onClick={() => setCollection('random')} className={`px-3 py-1.5 rounded-xl text-xs font-bold whitespace-nowrap transition-colors ${collection === 'random' ? 'bg-indigo-500 text-white' : 'bg-slate-100 text-slate-500'}`}>Acak</button>
                                <button onClick={() => setCollection('ml')} className={`px-3 py-1.5 rounded-xl text-xs font-bold whitespace-nowrap transition-colors ${collection === 'ml' ? 'bg-blue-500 text-white' : 'bg-slate-100 text-slate-500'}`}>Mobile Legends</button>
                                <button onClick={() => setCollection('jacob')} className={`px-3 py-1.5 rounded-xl text-xs font-bold whitespace-nowrap transition-colors ${collection === 'jacob' ? 'bg-emerald-500 text-white' : 'bg-slate-100 text-slate-500'}`}>Anak Yakub</button>
                            </div>

                            <div className="bg-slate-50 rounded-2xl p-3 border border-slate-100 mb-6 min-h-[150px]">
                                {collection === 'random' && (
                                    <div className="text-center py-4">
                                        <p className="text-xs text-slate-400 mb-3">Klik tombol di bawah untuk mengacak tampilan unikmu.</p>
                                        <button onClick={() => { setSeed(Math.random().toString(36)); setStyle('avataaars'); }} className="bg-white border border-slate-200 text-slate-600 px-4 py-2 rounded-xl text-xs font-bold shadow-sm hover:bg-slate-50 flex items-center gap-2 mx-auto">
                                            <RefreshCw size={14}/> Acak Avatar
                                        </button>
                                    </div>
                                )}

                                {collection === 'ml' && (
                                    <div className="grid grid-cols-4 gap-2">
                                        {ML_HEROES.map(hero => (
                                            <div key={hero} onClick={() => selectPreset(hero, 'micah')} className={`cursor-pointer rounded-xl p-1 border-2 transition-all ${seed === hero ? 'border-blue-500 bg-blue-50' : 'border-transparent hover:bg-white'}`}>
                                                <img src={`https://api.dicebear.com/7.x/micah/svg?seed=${hero}`} className="w-full h-full rounded-lg" alt={hero} />
                                                <p className="text-[8px] text-center font-bold text-slate-500 mt-1 truncate">{hero}</p>
                                            </div>
                                        ))}
                                    </div>
                                )}

                                {collection === 'jacob' && (
                                    <div className="grid grid-cols-4 gap-2">
                                        {JACOB_SONS.map(son => (
                                            <div key={son} onClick={() => selectPreset(son, 'adventurer')} className={`cursor-pointer rounded-xl p-1 border-2 transition-all ${seed === son ? 'border-emerald-500 bg-emerald-50' : 'border-transparent hover:bg-white'}`}>
                                                <img src={`https://api.dicebear.com/7.x/adventurer/svg?seed=${son}`} className="w-full h-full rounded-lg" alt={son} />
                                                <p className="text-[8px] text-center font-bold text-slate-500 mt-1 truncate">{son}</p>
                                            </div>
                                        ))}
                                    </div>
                                )}
                            </div>

                            <div className="mb-4">
                                <label className="block text-xs font-bold text-slate-400 uppercase tracking-wider mb-2 ml-1">
                                    {user.role === 'ADMIN' ? 'Ganti Password/PIN Admin' : 'PIN Keamanan (6 Digit)'}
                                </label>
                                <input type="text" maxLength="6" value={newPin} onChange={e => setNewPin(e.target.value.replace(/\D/g, ''))} className="w-full p-3 bg-slate-50 border border-slate-200 rounded-xl text-center font-bold text-slate-700 tracking-[0.5em] focus:ring-2 focus:ring-indigo-500 outline-none" placeholder="000000" />
                            </div>
                        </div>

                        <Button onClick={handleSave}>Simpan Profil</Button>
                    </div>
                </div>
            );
        };

        const MaterialModal = ({ user, onClose }) => {
            const [theme, setTheme] = useState('');
            const [verse, setVerse] = useState('');
            const [aiTopic, setAiTopic] = useState('');
            const [isGenerating, setIsGenerating] = useState(false);
            const handleSave = () => {
                if(!theme || !verse) return alert("Mohon isi Tema dan Ayat");
                DB.materials.save({
                    id: Date.now().toString(),
                    className: user.className,
                    teacherName: user.name,
                    theme,
                    verse,
                    createdAt: new Date().toISOString()
                });
                DB.activities.add(user.name, `Membuat materi: ${theme}`);
                alert("Materi berhasil disimpan!");
                onClose();
            };

            const handleGenerateAI = async () => {
                if (!aiTopic) return alert("Masukkan topik cerita Alkitab terlebih dahulu!");
                setIsGenerating(true);
                try {
                    const prompt = `Buatkan materi sekolah minggu singkat untuk anak sekolah dasar tentang topik: "${aiTopic}". Berikan output JSON dengan format: { "theme": "Judul Tema Menarik & Ceria", "verse": "Ayat Alkitab (Kitab Pasal:Ayat - Isi Singkat)" }. Gunakan Bahasa Indonesia yang mudah dipahami anak.`;
                    const result = await GeminiService.call(prompt);
                    if (result) {
                        setTheme(result.theme);
                        setVerse(result.verse);
                    }
                } catch (error) {
                    alert("Gagal menggunakan AI. Pastikan koneksi aman.");
                    console.error(error);
                } finally {
                    setIsGenerating(false);
                }
            };
            return (
                <div className="fixed inset-0 z-[60] flex items-center justify-center p-4">
                    <div className="absolute inset-0 bg-black/20 backdrop-blur-sm" onClick={onClose}></div>
                    <div className="bg-white rounded-[2rem] p-6 w-full max-w-sm relative z-10 shadow-2xl animate-pop">
                        <button onClick={onClose} className="absolute top-4 right-4 text-slate-400 hover:text-slate-600"><X size={24} /></button>
                        <div className="text-center mb-6">
                            <h3 className="text-xl font-bold text-slate-800">Materi Minggu Ini</h3>
                            <p className="text-slate-500 text-xs font-bold uppercase tracking-wider">{user.className}</p>
                        </div>

                        <div className="bg-gradient-to-r from-indigo-50 to-purple-50 p-4 rounded-2xl mb-4 border border-indigo-100">
                            <label className="block text-[10px] font-bold text-indigo-500 mb-1 uppercase tracking-wider flex items-center gap-1">
                                <Sparkles size={12}/> AI Assistant
                            </label>
                            <div className="flex gap-2">
                                <input value={aiTopic} onChange={e=>setAiTopic(e.target.value)} placeholder="Topik (misal: Kesabaran Ayub)" className="flex-1 p-2 bg-white border border-indigo-100 rounded-xl text-xs font-semibold outline-none focus:border-indigo-400"/>
                                <button onClick={handleGenerateAI} disabled={isGenerating} className="bg-indigo-500 text-white px-3 py-2 rounded-xl font-bold text-xs shadow-md hover:bg-indigo-600 disabled:opacity-50 transition-all flex items-center gap-1">
                                    {isGenerating ? <RefreshCw size={14} className="animate-spin"/> : <Zap size={14}/>}
                                    {isGenerating ? '...' : 'Buat'}
                                </button>
                            </div>
                        </div>

                        <div className="space-y-4 mb-6">
                            <div>
                                <label className="block text-xs font-bold text-slate-500 mb-1 ml-1">Tema Pengajaran</label>
                                <input value={theme} onChange={e=>setTheme(e.target.value)} placeholder="Contoh: Kasih Tuhan" className="w-full p-3 bg-slate-50 border border-slate-100 rounded-xl focus:ring-2 focus:ring-indigo-500 outline-none font-semibold text-slate-700"/>
                            </div>
                            <div>
                                <label className="block text-xs font-bold text-slate-500 mb-1 ml-1">Ayat Hafalan / Bacaan</label>
                                <textarea value={verse} onChange={e=>setVerse(e.target.value)} rows="3" placeholder="Contoh: Yohanes 3:16 - Karena begitu besar..." className="w-full p-3 bg-slate-50 border border-slate-100 rounded-xl focus:ring-2 focus:ring-indigo-500 outline-none font-semibold text-slate-700"></textarea>
                            </div>
                        </div>
                        <Button onClick={handleSave}>Publikasikan Materi</Button>
                    </div>
                </div>
            );
        };

        const LoginScreen = ({ onLogin }) => {
            const [mode, setMode] = useState('TEACHER');
            const [users, setUsers] = useState([]);
            const [selected, setSelected] = useState('');
            const [pw, setPw] = useState('');
            const [secretCount, setSecretCount] = useState(0);
            const [showAdmin, setShowAdmin] = useState(false); 
            const [showForgot, setShowForgot] = useState(false);
            const [recoveryKey, setRecoveryKey] = useState('');

            useEffect(() => setUsers(DB.get(STORAGE.USERS, DEFAULT_USERS)), []);
            const handleSecretTrigger = () => {
                if (showAdmin) return;
                const newCount = secretCount + 1;
                setSecretCount(newCount);
                if (newCount >= 5) {
                    setShowAdmin(true);
                    setMode('ADMIN');
                    alert("🔓 Admin Mode Terbuka!");
                }
            };
            const handleLogin = (e) => {
                e.preventDefault();
                
                const recordLogin = (loggedInUser) => {
                     const updated = { ...loggedInUser, lastLogin: new Date().toISOString() };
                     DB.users.update(updated);
                     DB.activities.add(loggedInUser.name, 'Login ke sistem');
                     onLogin(updated);
                };

                if (mode === 'ADMIN') {
                    if (pw === 'admin123') {
                        const adminUser = { id: 'admin', name: 'Administrator', role: 'ADMIN', lastLogin: new Date().toISOString() };
                        recordLogin(adminUser);
                    }
                    else alert('Password salah!');
                } else {
                    const u = users.find(x => x.id === selected);
                    if (u) {
                        if (u.isActive === false) return alert("Akun ini telah dinonaktifkan oleh Admin.");
                        if (u.pin && u.pin === pw) {
                            recordLogin(u);
                        } else {
                            alert('PIN Salah! Silakan coba lagi. (Default: 123456)');
                        }
                    } else {
                        alert('Silakan pilih nama pengguna terlebih dahulu.');
                    }
                }
            };

            const handleForgot = () => {
                if (recoveryKey === 'GKPS2025') { 
                    const admin = users.find(u => u.role === 'ADMIN');
                    if(admin) {
                        alert("Reset Berhasil! Password Admin kembali ke: admin123");
                        const updatedAdmin = { ...admin, pin: 'admin123' };
                        DB.users.update(updatedAdmin);
                    } else {
                        alert("Reset ke Default: Gunakan 'admin123'");
                    }
                    setShowForgot(false);
                } else {
                    alert("Recovery Key Salah!");
                }
            };

            const modes = showAdmin ? ['TEACHER', 'STUDENT', 'ADMIN'] : ['TEACHER', 'STUDENT'];
            return (
                <div className="min-h-screen flex flex-col items-center justify-center p-6 relative overflow-hidden">
                    <Background />
                    <div className="glass-panel p-8 rounded-[2.5rem] w-full max-w-sm animate-slide-up relative z-10">
                        <div className="flex justify-center mb-6">
                            <button onClick={handleSecretTrigger} className="w-20 h-20 bg-gradient-to-tr from-indigo-500 to-pink-500 rounded-3xl flex items-center justify-center shadow-xl shadow-indigo-500/20 animate-float active:scale-90 transition-transform cursor-pointer">
                                <Church className="text-white w-10 h-10" />
                            </button>
                        </div>
                        <div className="text-center mb-8">
                            <h1 className="text-2xl font-extrabold text-slate-800 tracking-tight mb-2 leading-tight">Presensi ASM-GSM<br/>GKPS Tangerang</h1>
                            <p className="text-slate-500 font-medium flex items-center justify-center gap-1"><Cloud size={14}/> Online Database System</p>
                        </div>
                        <div className="bg-white/50 p-1.5 rounded-2xl flex mb-6 backdrop-blur-sm">
                            {modes.map(m => (
                                <button key={m} onClick={() => { setMode(m); setSelected(''); setPw(''); }}
                                    className={`flex-1 py-3 text-[10px] font-bold rounded-xl transition-all ${mode === m ? 'bg-white text-indigo-600 shadow-md scale-100' : 'text-slate-400 hover:text-slate-600'}`}>
                                    {m === 'TEACHER' ? 'GURU' : m === 'STUDENT' ? 'SISWA' : 'ADMIN'}
                                </button>
                            ))}
                        </div>
                        <form onSubmit={handleLogin} className="space-y-4">
                            {mode !== 'ADMIN' ? (
                                <div className="space-y-3">
                                    <div className="relative group">
                                        <select value={selected} onChange={e => setSelected(e.target.value)}
                                            className="w-full p-4 pl-5 bg-white border border-slate-200 rounded-2xl outline-none focus:ring-2 focus:ring-indigo-500 font-bold text-slate-700 appearance-none shadow-sm transition-all hover:border-indigo-300">
                                            <option value="">Pilih Nama Anda...</option>
                                            {users.filter(u => u.role === mode && u.isActive !== false).map(u => <option key={u.id} value={u.id}>{u.name}</option>)}
                                        </select>
                                        <div className="absolute right-5 top-4 pointer-events-none text-slate-400"><ChevronRight className="rotate-90"/></div>
                                    </div>
                                    <input 
                                        type="password" 
                                        placeholder="Masukkan PIN (Default: 123456)" 
                                        value={pw} 
                                        onChange={e => setPw(e.target.value)}
                                        className="w-full p-4 bg-white border border-slate-200 rounded-2xl outline-none focus:ring-2 focus:ring-indigo-500 font-bold text-slate-700 shadow-sm" 
                                    />
                                </div>
                            ) : (
                                <div>
                                    <input type="password" placeholder="Password Admin" value={pw} onChange={e => setPw(e.target.value)}
                                        className="w-full p-4 bg-white border border-slate-200 rounded-2xl outline-none focus:ring-2 focus:ring-indigo-500 font-bold text-slate-700 shadow-sm" />
                                    <div className="text-right mt-2">
                                        <button type="button" onClick={() => setShowForgot(true)} className="text-xs text-indigo-500 font-bold hover:underline">Lupa Password?</button>
                                    </div>
                                </div>
                            )}
                            <Button variant="primary">Masuk Aplikasi <Sparkles size={18} /></Button>
                        </form>
                    </div>
                    <p className="absolute bottom-6 text-xs text-slate-400 font-medium opacity-60">GKPS Digital System v3.0 (Firebase)</p>

                    {showForgot && (
                        <div className="fixed inset-0 z-[80] flex items-center justify-center p-4 bg-black/40 backdrop-blur-sm">
                            <div className="bg-white p-6 rounded-3xl w-full max-w-xs animate-pop shadow-2xl">
                                <h3 className="text-lg font-bold text-slate-800 mb-2">Reset Password Admin</h3>
                                <p className="text-xs text-slate-500 mb-4">Masukkan Recovery Key dari Developer untuk mereset password ke default.</p>
                                <input value={recoveryKey} onChange={e=>setRecoveryKey(e.target.value)} placeholder="Recovery Key" className="w-full p-3 border rounded-xl text-sm font-bold mb-4 outline-none focus:border-indigo-500"/>
                                <div className="flex gap-2">
                                    <Button onClick={handleForgot}>Reset</Button>
                                    <Button variant="secondary" onClick={() => setShowForgot(false)}>Batal</Button>
                                </div>
                            </div>
                        </div>
                    )}
                </div>
            );
        };

        const UserManagement = () => {
            const [users, setUsers] = useState([]);
            const [search, setSearch] = useState('');
            const [form, setForm] = useState({ name: '', role: 'STUDENT', className: 'Kelas Daud', gender: 'Laki-Laki', pin: '123456' });
            const [isFormOpen, setIsFormOpen] = useState(false);
            const [isUploading, setIsUploading] = useState(false);
            const [editingId, setEditingId] = useState(null); 
            const fileInputRef = useRef(null);
            
            useEffect(() => { setUsers(DB.get(STORAGE.USERS, DEFAULT_USERS)); }, []);
            
            const handleSubmit = (e) => {
                e.preventDefault();
                if(!form.name) return;
                
                if (editingId) {
                    const updatedUser = { 
                        ...form, 
                        id: editingId,
                        ...users.find(u => u.id === editingId) 
                    };
                    updatedUser.name = form.name;
                    updatedUser.role = form.role;
                    updatedUser.className = (form.role === 'STUDENT' || form.role === 'TEACHER') ? form.className : '-';
                    updatedUser.gender = form.gender;
                    updatedUser.pin = form.pin;

                    DB.users.update(updatedUser);
                    alert("Data user berhasil diperbarui!");
                    setEditingId(null);
                } else {
                    const hasClass = form.role === 'STUDENT' || form.role === 'TEACHER';
                    const newUser = {
                        id: Date.now().toString(), 
                        name: form.name, 
                        role: form.role,
                        className: hasClass ? form.className : '-',
                        gender: form.gender,
                        pin: form.pin || '123456', 
                        qrCode: `${form.role.substring(0,1)}-${Date.now().toString().slice(-4)}`,
                        avatarStyle: 'avataaars',
                        isActive: true,
                        lastLogin: null
                    };
                    DB.users.add(newUser); 
                    alert(`User ${newUser.name} berhasil ditambahkan dengan PIN: ${newUser.pin}`);
                }
                
                const updated = DB.get(STORAGE.USERS);
                setUsers(updated);
                
                setForm({ name: '', role: 'STUDENT', className: 'Kelas Daud', gender: 'Laki-Laki', pin: '123456' });
                setIsFormOpen(false);
            };
            
            const handleEdit = (user) => {
                setForm({
                    name: user.name,
                    role: user.role,
                    className: user.className !== '-' ? user.className : 'Kelas Daud',
                    gender: user.gender,
                    pin: user.pin
                });
                setEditingId(user.id);
                setIsFormOpen(true);
            };

            const handleResetPin = (user) => {
                if(confirm(`Reset PIN untuk ${user.name} menjadi 123456?`)) {
                    const updatedUser = { ...user, pin: '123456' };
                    DB.users.update(updatedUser);
                    setUsers(DB.get(STORAGE.USERS));
                    alert("PIN berhasil direset!");
                }
            };

            const handleToggleStatus = (user) => {
                const newStatus = !user.isActive; 
                const action = newStatus ? "Mengaktifkan" : "Menonaktifkan";
                if(confirm(`${action} akun ${user.name}?`)) {
                    const updatedUser = { ...user, isActive: newStatus };
                    DB.users.update(updatedUser);
                    setUsers(DB.get(STORAGE.USERS));
                }
            };

            const handleImportClick = () => {
                fileInputRef.current.click();
            };

            const handleFileChange = (event) => {
                const file = event.target.files[0];
                if (!file) return;

                const reader = new FileReader();
                reader.onload = (e) => {
                    const text = e.target.result;
                    processCSV(text);
                };
                reader.readAsText(file);
                event.target.value = ''; 
            };

            const processCSV = async (csvText) => {
                setIsUploading(true);
                const lines = csvText.split('\n');
                let successCount = 0;
                
                for (let i = 0; i < lines.length; i++) {
                    const line = lines[i];
                    const [name, role, className, genderRaw] = line.split(',').map(item => item?.trim());
                    
                    if (name && role) {
                        const normalizedRole = role.toUpperCase();
                        if (['STUDENT', 'TEACHER', 'ADMIN'].includes(normalizedRole)) {
                             const hasClass = normalizedRole === 'STUDENT' || normalizedRole === 'TEACHER';
                             const finalClass = hasClass && className ? className : '-';
                             let finalGender = 'Laki-Laki';
                             if (genderRaw && (genderRaw.toLowerCase() === 'perempuan' || genderRaw.toLowerCase() === 'p' || genderRaw.toLowerCase() === 'pr')) {
                                 finalGender = 'Perempuan';
                             }
                             const newUser = {
                                id: Date.now().toString() + i, 
                                name: name, role: normalizedRole, className: finalClass, gender: finalGender,
                                pin: '123456', 
                                qrCode: `${normalizedRole.substring(0,1)}-${Date.now().toString().slice(-4)}-${i}`,
                                avatarStyle: 'avataaars',
                                isActive: true
                            };
                            try {
                                await pushToFirestore('users', newUser, newUser.id);
                                const currentUsers = JSON.parse(localStorage.getItem(STORAGE.USERS)) || [];
                                currentUsers.push(newUser);
                                localStorage.setItem(STORAGE.USERS, JSON.stringify(currentUsers));
                                successCount++;
                            } catch (err) {
                                console.error("Gagal upload user:", name, err);
                            }
                        }
                    }
                }

                if (successCount > 0) {
                    setUsers(DB.get(STORAGE.USERS));
                    DB.activities.add('Admin', `Import ${successCount} user baru via CSV`);
                    alert(`SUKSES! ${successCount} data berhasil diupload ke Cloud. Silakan buka HP Anda.`);
                } else {
                    alert("Gagal membaca data. Gunakan format: Nama,Role,Kelas,Gender");
                }
                setIsUploading(false);
            };
            const handleDelete = (id) => {
                if(window.confirm('Hapus user ini?')) {
                    DB.users.delete(id);
                    const updated = DB.get(STORAGE.USERS);
                    setUsers(updated);
                    DB.activities.add('Admin', `Menghapus user ID: ${id}`);
                }
            };

            const filtered = users.filter(u => u.name.toLowerCase().includes(search.toLowerCase()));
            return (
                <div className="p-6 pb-32 animate-slide-up">
                    <div className="flex justify-between items-center mb-6">
                        <h2 className="text-2xl font-extrabold text-slate-800">Manajemen User</h2>
                        <div className="flex gap-2">
                            <input type="file" ref={fileInputRef} onChange={handleFileChange} className="hidden" accept=".csv" />
                            <button onClick={handleImportClick} disabled={isUploading} className="bg-emerald-50 backdrop-blur border border-emerald-100 p-2 px-3 rounded-xl text-xs font-bold text-emerald-600 shadow-sm flex items-center gap-1 hover:bg-emerald-100 transition-colors">
                                {isUploading ? <RefreshCw size={14} className="animate-spin"/> : <Upload size={14}/>} 
                                <span className="hidden md:inline">{isUploading ? 'Mengupload...' : 'Import'}</span>
                            </button>
                            <button onClick={() => { setIsFormOpen(!isFormOpen); setEditingId(null); setForm({name: '', role: 'STUDENT', className: 'Kelas Daud', gender: 'Laki-Laki', pin: '123456'}); }} className="bg-white/80 backdrop-blur border border-white p-2 px-3 rounded-xl text-xs font-bold text-indigo-600 shadow-sm flex items-center gap-1 hover:bg-indigo-50 transition-colors">
                                {isFormOpen ? <><X size={14}/> <span className="hidden md:inline">Tutup</span></> : <><Plus size={14}/> <span className="hidden md:inline">Tambah</span></>}
                            </button>
                        </div>
                    </div>

                    {isFormOpen && (
                        <div className="glass-card p-5 rounded-[2rem] mb-6 animate-pop">
                            <h3 className="font-bold text-slate-700 mb-4">{editingId ? 'Edit Data User' : 'Data User Baru'}</h3>
                            <div className="space-y-3">
                                <input value={form.name} onChange={e => setForm({...form, name: e.target.value})} placeholder="Nama Lengkap" className="w-full p-3 rounded-xl bg-white/50 border border-white focus:ring-2 focus:ring-indigo-500 outline-none font-semibold text-slate-700 placeholder-slate-400" />
                                <input value={form.pin} onChange={e => setForm({...form, pin: e.target.value})} placeholder="Set PIN (Default: 123456)" className="w-full p-3 rounded-xl bg-white/50 border border-white focus:ring-2 focus:ring-indigo-500 outline-none font-semibold text-slate-700 placeholder-slate-400" />
                                <div className="grid grid-cols-1 md:grid-cols-2 gap-2">
                                    <div className="relative">
                                        <select value={form.gender} onChange={e => setForm({...form, gender: e.target.value})} className="w-full p-3 rounded-xl bg-white/50 border border-white outline-none font-semibold text-slate-600 text-sm appearance-none">
                                            <option value="Laki-Laki">Laki-Laki</option>
                                            <option value="Perempuan">Perempuan</option>
                                        </select>
                                        <ChevronRight className="absolute right-3 top-3.5 rotate-90 text-slate-400 w-4 h-4 pointer-events-none"/>
                                    </div>
                                    <div className="relative">
                                        <select value={form.role} onChange={e => setForm({...form, role: e.target.value})} className="w-full p-3 rounded-xl bg-white/50 border border-white outline-none font-semibold text-slate-600 text-sm appearance-none">
                                            <option value="STUDENT">Siswa</option><option value="TEACHER">Guru</option><option value="ADMIN">Admin</option>
                                        </select>
                                        <ChevronRight className="absolute right-3 top-3.5 rotate-90 text-slate-400 w-4 h-4 pointer-events-none"/>
                                    </div>
                                </div>
                                {(form.role === 'STUDENT' || form.role === 'TEACHER') && (
                                    <div className="relative">
                                        <select value={form.className} onChange={e => setForm({...form, className: e.target.value})} className="w-full p-3 rounded-xl bg-white/50 border border-white outline-none font-semibold text-slate-600 text-sm appearance-none">
                                            {DEFAULT_CLASSES.map(c => <option key={c.id} value={c.name}>{c.name}</option>)}
                                        </select>
                                        <ChevronRight className="absolute right-3 top-3.5 rotate-90 text-slate-400 w-4 h-4 pointer-events-none"/>
                                    </div>
                                )}
                                <Button onClick={handleSubmit}>{editingId ? 'Update Data' : 'Simpan Data'}</Button>
                            </div>
                        </div>
                    )}

                    <div className="relative mb-6">
                        <Search className="absolute left-4 top-3.5 text-slate-400" size={20}/>
                        <input value={search} onChange={e => setSearch(e.target.value)} placeholder="Cari nama user..." className="w-full p-3 pl-12 rounded-2xl bg-white/60 border border-white/40 focus:bg-white transition-all outline-none font-medium text-slate-700 placeholder-slate-400" />
                    </div>

                    <div className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-4">
                        {filtered.length === 0 ? <div className="col-span-full text-center py-10 text-slate-400 font-medium">Tidak ada user ditemukan</div> : filtered.map(u => (
                            <div key={u.id} className={`glass-card p-4 rounded-2xl flex flex-col gap-3 group animate-pop hover:shadow-lg transition-all ${u.isActive === false ? 'opacity-60 grayscale' : ''}`}>
                                <div className="flex items-center justify-between w-full">
                                    <div className="flex items-center gap-3">
                                        <Avatar name={u.name} seed={u.avatarSeed} style={u.avatarStyle} size="sm" />
                                        <div>
                                            <p className="font-bold text-slate-800 text-sm">{u.name}</p>
                                            <div className="flex items-center gap-2 mt-0.5 flex-wrap">
                                                <span className={`text-[10px] font-bold px-2 py-0.5 rounded-md ${u.role === 'ADMIN' ? 'bg-rose-100 text-rose-600' : u.role === 'TEACHER' ? 'bg-amber-100 text-amber-600' : 'bg-indigo-100 text-indigo-600'}`}>{u.role}</span>
                                                <span className={`text-[10px] font-bold px-2 py-0.5 rounded-md ${u.gender === 'Perempuan' ? 'bg-pink-100 text-pink-600' : 'bg-blue-100 text-blue-600'}`}>{u.gender === 'Perempuan' ? 'P' : 'L'}</span>
                                                {(u.role === 'STUDENT' || u.role === 'TEACHER') && <span className="text-[10px] text-slate-400 font-medium">• {u.className}</span>}
                                            </div>
                                        </div>
                                    </div>
                                    <div className="flex gap-1">
                                        <button onClick={() => handleEdit(u)} className="w-8 h-8 flex items-center justify-center rounded-full bg-blue-50 text-blue-500 hover:bg-blue-100 transition-colors" title="Edit User"><Edit size={14}/></button>
                                        <button onClick={() => handleDelete(u.id)} className="w-8 h-8 flex items-center justify-center rounded-full bg-red-50 text-red-500 hover:bg-red-100 transition-colors" title="Hapus User"><Trash2 size={14}/></button>
                                    </div>
                                </div>
                                
                                <div className="grid grid-cols-2 gap-2 border-t border-slate-100 pt-3">
                                    <button onClick={() => handleResetPin(u)} className="flex items-center justify-center gap-1.5 py-1.5 rounded-lg bg-slate-50 text-[10px] font-bold text-slate-600 hover:bg-slate-100">
                                        <Key size={12}/> Reset PIN
                                    </button>
                                    <button onClick={() => handleToggleStatus(u)} className={`flex items-center justify-center gap-1.5 py-1.5 rounded-lg text-[10px] font-bold ${u.isActive !== false ? 'bg-emerald-50 text-emerald-600 hover:bg-emerald-100' : 'bg-slate-200 text-slate-500 hover:bg-slate-300'}`}>
                                        {u.isActive !== false ? <><Power size={12}/> Aktif</> : <><Power size={12}/> Nonaktif</>}
                                    </button>
                                </div>
                            </div>
                        ))}
                    </div>
                </div>
            );
        };

        const Dashboard = ({ user }) => {
            // FIX: GUNAKAN getLocalDate() AGAR TANGGAL DEFAULT SESUAI JAM LOKAL
            const [date, setDate] = useState(getLocalDate());
            const [att, setAtt] = useState([]);
            const [activities, setActivities] = useState([]);
            const [users, setUsers] = useState([]);
            const [isMatModalOpen, setIsMatModalOpen] = useState(false);
            const [isSchedModalOpen, setIsSchedModalOpen] = useState(false);
            
            const [bcTitle, setBcTitle] = useState('');
            const [bcMsg, setBcMsg] = useState('');
            // FIX: GUNAKAN getLocalDate()
            const [bcDate, setBcDate] = useState(getLocalDate()); 
            const [bcTime, setBcTime] = useState(new Date().toTimeString().slice(0,5)); 
            const [pendingBroadcasts, setPendingBroadcasts] = useState([]); 

            const [aiAnalysis, setAiAnalysis] = useState(null);
            const [isAnalyzing, setIsAnalyzing] = useState(false);
            const [aiDevotional, setAiDevotional] = useState(null);
            const [loadingDevo, setLoadingDevo] = useState(false);
            
            // FIX: Tambahkan Real-time Listener (onSnapshot)
            useEffect(() => {
                // Listener untuk Presensi
                if (!auth.currentUser) return; // Guard clause

                const unsubscribeAtt = onSnapshot(getCollectionRef('attendance'), (snapshot) => {
                    const data = snapshot.docs.map(doc => doc.data());
                    localStorage.setItem(STORAGE.ATTENDANCE, JSON.stringify(data));
                    setAtt(data.filter(r => r.date === date));
                }, (error) => {
                    console.error("Error fetching attendance:", error);
                });

                // Listener untuk Aktivitas
                const unsubscribeAct = onSnapshot(getCollectionRef('activities'), (snapshot) => {
                    const data = snapshot.docs.map(doc => doc.data());
                    // Sort descending
                    data.sort((a,b) => new Date(b.timestamp) - new Date(a.timestamp));
                    localStorage.setItem(STORAGE.ACTIVITIES, JSON.stringify(data));
                    setActivities(data);
                }, (error) => {
                    console.error("Error fetching activities:", error);
                });

                let unsubscribeUsers = () => {};
                // Admin perlu live update user untuk melihat status login
                if (user.role === 'ADMIN') {
                     unsubscribeUsers = onSnapshot(getCollectionRef('users'), (snapshot) => {
                        const data = snapshot.docs.map(doc => doc.data());
                        localStorage.setItem(STORAGE.USERS, JSON.stringify(data));
                        setUsers(data);
                    }, (error) => {
                        console.error("Error fetching users:", error);
                    });
                } else {
                    // Non-admin load from LS normally
                    setUsers(DB.get(STORAGE.USERS, DEFAULT_USERS));
                }

                // Initial load from LS for immediate display before sync
                const allAtt = DB.get(STORAGE.ATTENDANCE, []);
                setAtt(allAtt.filter(r => r.date === date));
                setActivities(DB.activities.get());
                
                // Load Pending Broadcasts
                const allNotifs = DB.notifications.get();
                setPendingBroadcasts(allNotifs.filter(n => n.status === 'scheduled' && new Date(n.scheduledTime) > new Date()));

                return () => {
                    if(unsubscribeAtt) unsubscribeAtt();
                    if(unsubscribeAct) unsubscribeAct();
                    if(unsubscribeUsers) unsubscribeUsers();
                };
            }, [date, user.role]); 

            const stats = useMemo(() => {
                const grouped = {};
                att.filter(x => x.role === 'STUDENT').forEach(x => grouped[x.className] = (grouped[x.className] || 0) + 1);
                return Object.entries(grouped).map(([k,v]) => ({ name: k, value: v }));
            }, [att]);
            const weeklyData = [
                { name: 'Sen', hadir: 12 }, { name: 'Sel', hadir: 15 }, { name: 'Rab', hadir: 8 },
                { name: 'Kam', hadir: 20 }, { name: 'Jum', hadir: 18 }, { name: 'Sab', hadir: 25 }, { name: 'Min', hadir: 40 }
            ];

            const handleBroadcast = () => {
                if(!bcTitle || !bcMsg) return alert("Mohon isi judul dan pesan");
                
                const scheduleDateTime = new Date(`${bcDate}T${bcTime}`);
                const isScheduled = scheduleDateTime > new Date();
                
                DB.notifications.broadcast(bcTitle, bcMsg, user.name, scheduleDateTime.toISOString());
                
                const actionText = isScheduled ? `Menjadwalkan broadcast: ${bcTitle} pada ${scheduleDateTime.toLocaleString()}` : `Mengirim broadcast: ${bcTitle}`;
                DB.activities.add(user.name, actionText);
                
                setBcTitle(''); setBcMsg('');
                
                const allNotifs = DB.notifications.get();
                setPendingBroadcasts(allNotifs.filter(n => n.status === 'scheduled' && new Date(n.scheduledTime) > new Date()));

                alert(isScheduled ? "Broadcast berhasil dijadwalkan!" : "Broadcast berhasil dikirim!");
            };

            const handleAnalyze = async () => {
                setIsAnalyzing(true);
                try {
                    const prompt = `Analisa data absensi berikut dan berikan insight singkat (maks 3 kalimat) serta 1 rekomendasi konkret.
                    Total Siswa: ${users.filter(u => u.role === 'STUDENT').length}. Hadir Hari Ini: ${att.length}. Kelas dengan kehadiran tertinggi: ${stats.sort((a,b)=>b.value-a.value)[0]?.name || '-'}.
                    Format output JSON: { "insight": "...", "recommendation": "..." }`;
                    const result = await GeminiService.call(prompt);
                    if (result) setAiAnalysis(result);
                } catch (error) {
                    console.error("AI Error", error);
                    alert("Gagal melakukan analisa AI.");
                } finally {
                    setIsAnalyzing(false);
                }
            };
            const generateDevotional = async () => {
                setLoadingDevo(true);
                try {
                    const prompt = "Berikan satu renungan singkat dan motivasi untuk guru sekolah minggu yang inspiratif. Format JSON: { \"title\": \"Judul\", \"content\": \"Isi Renungan\" }";
                    const res = await GeminiService.call(prompt);
                    if(res) setAiDevotional(res);
                } catch(e) { console.error(e); } finally { setLoadingDevo(false);
                }
            };
            
            const handleExportExcel = () => {
                const allAtt = DB.get(STORAGE.ATTENDANCE, []);
                if(allAtt.length === 0) return alert("Belum ada data absensi untuk diexport.");
                const ws = XLSX.utils.json_to_sheet(allAtt.map(a => ({
                    Tanggal: a.date, Waktu: new Date(a.timestamp).toLocaleTimeString(), Nama: a.userName, Role: a.role, Kelas: a.className
                })));
                const wb = XLSX.utils.book_new();
                XLSX.utils.book_append_sheet(wb, ws, "Kehadiran");
                XLSX.writeFile(wb, "Laporan_Kehadiran_GKPS.xlsx");
            };
            const handleExportPDF = () => {
                 const allAtt = DB.get(STORAGE.ATTENDANCE, []);
                 if(allAtt.length === 0) return alert("Belum ada data absensi untuk diexport.");
                 const doc = new jspdf.jsPDF();
                 doc.text("Laporan Kehadiran Sekolah Minggu GKPS", 14, 20);
                 doc.setFontSize(10);
                 doc.text(`Dicetak pada: ${new Date().toLocaleString()}`, 14, 28);
                 const tableColumn = ["Tanggal", "Waktu", "Nama", "Role", "Kelas"];
                 const tableRows = [];
                 allAtt.forEach(a => {
                     const row = [a.date, new Date(a.timestamp).toLocaleTimeString(), a.userName, a.role, a.className];
                     tableRows.push(row);
                 });
                 doc.autoTable({ head: [tableColumn], body: tableRows, startY: 35 });
                 doc.save("Laporan_Kehadiran_GKPS.pdf");
            };

            const COLORS = ['#6366f1', '#ec4899', '#a855f7', '#f43f5e'];
            
            const recentLogins = useMemo(() => {
                return users
                    .filter(u => u.lastLogin)
                    .sort((a,b) => new Date(b.lastLogin) - new Date(a.lastLogin))
                    .slice(0, 5); 
            }, [users]); 

            if (user.role === 'ADMIN') {
                const studentCount = users.filter(u => u.role === 'STUDENT').length;
                const teacherCount = users.filter(u => u.role === 'TEACHER').length;

                return (
                    <div className="p-6 pb-32 animate-slide-up">
                        <header className="mb-8 flex justify-between items-center">
                            <div>
                                <p className="text-slate-500 font-medium text-sm mb-1 uppercase tracking-wider">Dashboard</p>
                                <h2 className="text-3xl font-extrabold text-slate-800">Admin Control</h2>
                            </div>
                            <div className="hidden md:flex items-center gap-2 bg-white px-4 py-2 rounded-2xl shadow-sm">
                                <Calendar size={18} className="text-indigo-500" />
                                <span className="text-sm font-bold text-slate-600">{new Date().toLocaleDateString('id-ID', { 
                                    weekday: 'long', year: 'numeric', month: 'long', day: 'numeric' })}</span>
                            </div>
                        </header>

                        <div className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-4 mb-8">
                            <div className="glass-card p-5 rounded-3xl relative overflow-hidden group hover:shadow-lg transition-shadow">
                                <div className="absolute right-[-10px] top-[-10px] w-20 h-20 bg-blue-100 rounded-full opacity-50 group-hover:scale-110 transition-transform"></div>
                                <div className="flex items-center gap-3 mb-2">
                                    <div className="p-2 bg-blue-50 text-blue-600 rounded-xl"><GraduationCap size={24}/></div>
                                    <p className="text-slate-500 font-bold text-xs uppercase tracking-wider">Total Siswa</p>
                                </div>
                                <h3 className="text-3xl font-black text-slate-800">{studentCount}</h3>
                                <p className="text-xs text-blue-500 font-medium mt-1">Terdaftar Aktif</p>
                            </div>
                            <div className="glass-card p-5 rounded-3xl relative overflow-hidden group hover:shadow-lg transition-shadow">
                                <div className="absolute right-[-10px] top-[-10px] w-20 h-20 bg-amber-100 rounded-full opacity-50 group-hover:scale-110 transition-transform"></div>
                                <div className="flex items-center gap-3 mb-2">
                                    <div className="p-2 bg-amber-50 text-amber-600 rounded-xl"><Briefcase size={24}/></div>
                                    <p className="text-slate-500 font-bold text-xs uppercase tracking-wider">Total Guru</p>
                                </div>
                                <h3 className="text-3xl font-black text-slate-800">{teacherCount}</h3>
                                <p className="text-xs text-amber-500 font-medium mt-1">Pengajar Aktif</p>
                            </div>
                            <div className="glass-card p-5 rounded-3xl relative overflow-hidden group hover:shadow-lg transition-shadow">
                                <div className="absolute right-[-10px] top-[-10px] w-20 h-20 bg-emerald-100 rounded-full opacity-50 group-hover:scale-110 transition-transform"></div>
                                <div className="flex items-center gap-3 mb-2">
                                    <div className="p-2 bg-emerald-50 text-emerald-600 rounded-xl"><CheckCircle size={24}/></div>
                                    <p className="text-slate-500 font-bold text-xs uppercase tracking-wider">Hadir Hari Ini</p>
                                </div>
                                <h3 className="text-3xl font-black text-slate-800">{att.length}</h3>
                                <p className="text-xs text-emerald-500 font-medium mt-1">Siswa & Guru</p>
                            </div>
                            <div className="glass-card p-5 rounded-3xl relative overflow-hidden group hover:shadow-lg transition-shadow">
                                <div className="absolute right-[-10px] top-[-10px] w-20 h-20 bg-indigo-100 rounded-full opacity-50 group-hover:scale-110 transition-transform"></div>
                                <div className="flex items-center gap-3 mb-2">
                                    <div className="p-2 bg-indigo-50 text-indigo-600 rounded-xl"><Church size={24}/></div>
                                    <p className="text-slate-500 font-bold text-xs uppercase tracking-wider">Total Kelas</p>
                                </div>
                                <h3 className="text-3xl font-black text-slate-800">{DEFAULT_CLASSES.length}</h3>
                                <p className="text-xs text-indigo-500 font-medium mt-1">Ruang Belajar</p>
                            </div>
                        </div>

                        <div className="mb-8 flex gap-4">
                            <button onClick={handleExportExcel} className="flex-1 bg-green-600 text-white p-4 rounded-2xl shadow-lg hover:bg-green-700 transition-all flex items-center justify-center gap-2 font-bold">
                                <FileSpreadsheet size={24}/> Export Excel
                            </button>
                            <button onClick={handleExportPDF} className="flex-1 bg-red-600 text-white p-4 rounded-2xl shadow-lg hover:bg-red-700 transition-all flex items-center justify-center gap-2 font-bold">
                                <File size={24}/> Export PDF
                            </button>
                        </div>
                        
                        <div className="mb-8">
                             <h3 className="font-bold text-slate-700 mb-4 flex items-center gap-2">
                                <Eye size={20} className="text-indigo-500"/> Pantauan Login User (5 Terakhir)
                            </h3>
                            <div className="glass-card p-0 rounded-[1.5rem] overflow-hidden">
                                <div className="overflow-x-auto">
                                    <table className="w-full text-left text-sm text-slate-600">
                                        <thead className="bg-slate-50 border-b border-slate-100">
                                            <tr>
                                                <th className="p-4 font-bold text-xs uppercase tracking-wider">User</th>
                                                <th className="p-4 font-bold text-xs uppercase tracking-wider">Role</th>
                                                <th className="p-4 font-bold text-xs uppercase tracking-wider">Waktu Login</th>
                                            </tr>
                                        </thead>
                                        <tbody className="divide-y divide-slate-100">
                                            {recentLogins.length > 0 ? recentLogins.map(u => (
                                                <tr key={u.id} className="hover:bg-slate-50/50">
                                                    <td className="p-4 font-bold text-slate-800">{u.name}</td>
                                                    <td className="p-4">
                                                        <span className={`px-2 py-0.5 rounded text-[10px] font-bold ${
                                                            u.role === 'ADMIN' ? 'bg-rose-100 text-rose-600' : 
                                                            u.role === 'TEACHER' ? 'bg-amber-100 text-amber-600' : 'bg-indigo-100 text-indigo-600'
                                                        }`}>{u.role}</span>
                                                    </td>
                                                    <td className="p-4 text-xs font-mono">{new Date(u.lastLogin).toLocaleString()}</td>
                                                </tr>
                                            )) : (
                                                <tr><td colSpan="3" className="p-4 text-center text-slate-400">Belum ada data login baru.</td></tr>
                                            )}
                                        </tbody>
                                    </table>
                                </div>
                            </div>
                        </div>

                        <div className="mb-8">
                            <div className="glass-card p-6 rounded-[2rem] bg-gradient-to-r from-purple-500 to-indigo-600 text-white relative overflow-hidden">
                                <div className="absolute top-0 right-0 w-64 h-64 bg-white opacity-10 rounded-full blur-3xl -mr-16 -mt-16"></div>
                                <div className="relative z-10">
                                    <div className="flex justify-between items-start mb-4">
                                        <div>
                                            <h3 className="text-2xl font-bold flex items-center gap-2"><BrainCircuit size={24}/> Analisa Cerdas AI</h3>
                                            <p className="text-indigo-100 text-sm mt-1">Dapatkan wawasan mendalam tentang data kehadiran.</p>
                                        </div>
                                        <button onClick={handleAnalyze} disabled={isAnalyzing} className="bg-white text-indigo-600 px-4 py-2 rounded-xl font-bold text-sm shadow-lg hover:bg-indigo-50 transition-colors disabled:opacity-70 flex items-center gap-2">
                                            {isAnalyzing ? <RefreshCw size={16} className="animate-spin"/> : <Sparkles size={16}/>}
                                            {isAnalyzing ? 'Menganalisa...' : 'Analisa Sekarang'}
                                        </button>
                                    </div>
                                    {aiAnalysis && (
                                        <div className="bg-white/10 backdrop-blur-md rounded-xl p-4 border border-white/20 animate-slide-up">
                                            <div className="mb-3">
                                                <p className="text-xs font-bold text-indigo-200 uppercase mb-1">Insight</p>
                                                <p className="text-sm font-medium leading-relaxed">{aiAnalysis.insight}</p>
                                            </div>
                                            <div>
                                                <p className="text-xs font-bold text-emerald-200 uppercase mb-1">Rekomendasi</p>
                                                <p className="text-sm font-medium leading-relaxed">{aiAnalysis.recommendation}</p>
                                            </div>
                                        </div>
                                    )}
                                </div>
                            </div>
                        </div>

                        <div className="grid grid-cols-1 lg:grid-cols-3 gap-6 mb-8">
                            <div className="lg:col-span-2 space-y-6">
                                <div className="glass-card p-6 rounded-[2rem]">
                                    <div className="flex justify-between items-center mb-6">
                                        <h3 className="font-bold text-slate-700 flex items-center gap-2">
                                            <TrendingUp size={20} className="text-indigo-500"/> Tren Kehadiran Mingguan
                                        </h3>
                                    </div>
                                    <div className="h-64 w-full">
                                        <ResponsiveContainer width="100%" height="100%">
                                            <BarChart data={weeklyData}>
                                                <CartesianGrid strokeDasharray="3 3" vertical={false} stroke="#e2e8f0" />
                                                <XAxis dataKey="name" axisLine={false} tickLine={false} tick={{fill: '#64748b', fontSize: 12}} dy={10} />
                                                <Tooltip cursor={{fill: '#f1f5f9'}} contentStyle={{borderRadius: '12px', border: 'none', boxShadow: '0 10px 30px rgba(0,0,0,0.1)'}} />
                                                <Bar dataKey="hadir" fill="#6366f1" radius={[6, 6, 0, 0]} barSize={32} />
                                            </BarChart>
                                        </ResponsiveContainer>
                                    </div>
                                </div>

                                <div className="glass-card p-6 rounded-[2rem] border-l-4 border-l-pink-500">
                                    <h3 className="font-bold text-slate-700 mb-4 flex items-center gap-2"><Radio size={20} className="text-pink-500"/> Kirim Pengumuman (Broadcast)</h3>
                                    <div className="space-y-4">
                                        <div className="bg-slate-50 p-4 rounded-2xl border border-slate-100">
                                            <input value={bcTitle} onChange={e=>setBcTitle(e.target.value)} placeholder="Judul Pengumuman" className="w-full bg-transparent outline-none font-bold text-slate-700 mb-2 border-b border-slate-200 pb-2 focus:border-pink-500 transition-colors"/>
                                            <textarea value={bcMsg} onChange={e=>setBcMsg(e.target.value)} rows="2" placeholder="Tulis pesan untuk semua guru dan murid..." className="w-full bg-transparent outline-none text-slate-600 text-sm resize-none mb-3"></textarea>
                                            
                                            <div className="flex items-center gap-2 pt-2 border-t border-slate-200">
                                                <span className="text-xs font-bold text-slate-400 uppercase tracking-wider">Jadwalkan:</span>
                                                <input type="date" value={bcDate} onChange={e=>setBcDate(e.target.value)} className="bg-white border border-slate-200 rounded-lg px-2 py-1 text-xs font-bold text-slate-600"/>
                                                <input type="time" value={bcTime} onChange={e=>setBcTime(e.target.value)} className="bg-white border border-slate-200 rounded-lg px-2 py-1 text-xs font-bold text-slate-600"/>
                                            </div>
                                        </div>
                                        <div className="flex justify-between items-center">
                                            <p className="text-xs text-slate-400 italic">
                                                *Set waktu ke masa depan untuk menjadwalkan.
                                            </p>
                                            <button onClick={handleBroadcast} className="bg-pink-500 text-white px-6 py-2 rounded-xl font-bold shadow-lg shadow-pink-500/30 active:scale-95 transition-all flex items-center gap-2">
                                                Kirim / Jadwalkan <Send size={16}/>
                                            </button>
                                        </div>
                                    </div>

                                    {pendingBroadcasts.length > 0 && (
                                        <div className="mt-4 pt-4 border-t border-slate-100">
                                            <h4 className="text-xs font-bold text-slate-500 uppercase mb-2 flex items-center gap-1"><Timer size={12}/> Antrean Broadcast Terjadwal</h4>
                                            <div className="space-y-2">
                                                {pendingBroadcasts.map(pb => (
                                                    <div key={pb.id} className="bg-yellow-50 border border-yellow-100 p-2 rounded-xl flex justify-between items-center">
                                                        <div>
                                                            <p className="text-xs font-bold text-slate-700">{pb.title}</p>
                                                            <p className="text-[10px] text-slate-500">Tayang: {new Date(pb.scheduledTime).toLocaleString()}</p>
                                                        </div>
                                                        <span className="text-[10px] font-bold bg-yellow-100 text-yellow-700 px-2 py-1 rounded">Waiting</span>
                                                    </div>
                                                ))}
                                            </div>
                                        </div>
                                    )}
                                </div>
                            </div>

                            <div className="space-y-6">
                                <div className="glass-card p-6 rounded-[2rem]">
                                    <h3 className="font-bold text-slate-700 mb-4">Proporsi Kelas</h3>
                                    <div className="h-48 w-full relative">
                                        {stats.length > 0 ? (
                                            <ResponsiveContainer>
                                                <PieChart>
                                                    <Pie data={stats} innerRadius={50} outerRadius={70} paddingAngle={5} dataKey="value">
                                                        {stats.map((_, i) => <Cell key={i} fill={COLORS[i % COLORS.length]} strokeWidth={0} />)}
                                                    </Pie>
                                                    <Tooltip />
                                                </PieChart>
                                            </ResponsiveContainer>
                                        ) : (
                                            <div className="absolute inset-0 flex flex-col items-center justify-center text-slate-400">
                                                <p className="text-xs">Belum ada data hari ini</p>
                                            </div>
                                        )}
                                    </div>
                                </div>

                                <div className="glass-card p-6 rounded-[2rem] h-[400px] flex flex-col">
                                    <h3 className="font-bold text-slate-700 mb-4 flex items-center gap-2"><Activity size={20} className="text-indigo-500"/> Log Aktivitas</h3>
                                    <div className="flex-1 overflow-y-auto space-y-4 pr-2">
                                        {activities.map((act, i) => (
                                            <div key={act.id} className="flex gap-3 relative pb-4 border-l-2 border-slate-100 last:border-0 pl-4 last:pb-0">
                                                <div className="absolute -left-[9px] top-0 w-4 h-4 bg-white border-2 border-indigo-500 rounded-full"></div>
                                                <div>
                                                    <p className="text-xs font-bold text-slate-800">{act.userName}</p>
                                                    <p className="text-[11px] text-slate-500 leading-tight mb-1">{act.action}</p>
                                                    <span className="text-[10px] text-indigo-400 font-medium bg-indigo-50 px-2 py-0.5 rounded-md">
                                                        {new Date(act.timestamp).toLocaleTimeString([], {hour:'2-digit', minute:'2-digit'})}
                                                    </span>
                                                </div>
                                            </div>
                                        ))}
                                        {activities.length === 0 && <p className="text-center text-slate-400 text-xs mt-10">Belum ada aktivitas.</p>}
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>
                );
            }

            return (
                <div className="p-6 pb-32 animate-slide-up">
                    <header className="flex justify-between items-center mb-8">
                        <div>
                            <p className="text-slate-500 font-medium text-sm mb-1">Overview</p>
                            <h2 className="text-3xl font-extrabold text-slate-800">Statistik</h2>
                        </div>
                        <div className="flex items-center gap-2">
                             {user.role === 'TEACHER' && (
                                <button onClick={generateDevotional} className="bg-gradient-to-tr from-yellow-400 to-orange-500 text-white p-2 rounded-xl shadow-lg hover:scale-105 transition-transform" title="Renungan Harian Guru AI">
                                    {loadingDevo ? <RefreshCw size={20} className="animate-spin"/> : <Sparkles size={20}/>}
                                </button>
                             )}
                            <div className="bg-white p-2 rounded-2xl shadow-sm border border-slate-100 flex items-center gap-2">
                                <Calendar size={18} className="text-indigo-500 ml-2" />
                                <input type="date" value={date} onChange={e => setDate(e.target.value)} className="bg-transparent font-bold text-slate-600 outline-none text-sm w-32" />
                            </div>
                        </div>
                    </header>

                    {aiDevotional && user.role === 'TEACHER' && (
                        <div className="mb-6 bg-gradient-to-r from-yellow-50 to-orange-50 p-4 rounded-2xl border border-orange-100 shadow-sm animate-pop relative overflow-hidden">
                            <div className="absolute top-0 right-0 w-16 h-16 bg-yellow-200 rounded-full blur-2xl opacity-50 -mr-4 -mt-4"></div>
                            <div className="relative z-10">
                                <h4 className="font-bold text-orange-600 text-sm flex items-center gap-2 mb-1">
                                    <Sparkles size={12}/> {aiDevotional.title} (Edisi Guru)
                                </h4>
                                <p className="text-xs text-slate-700 italic">"{aiDevotional.content}"</p>
                            </div>
                            <button onClick={()=>setAiDevotional(null)} className="absolute top-2 right-2 text-orange-300 hover:text-orange-500"><X size={14}/></button>
                        </div>
                    )}

                    {user.role === 'TEACHER' && (
                        <div className="grid grid-cols-1 md:grid-cols-2 gap-4 mb-6">
                            <div onClick={() => setIsMatModalOpen(true)} className="glass-card p-5 rounded-3xl bg-gradient-to-r from-indigo-500 to-purple-500 text-white cursor-pointer hover:shadow-xl hover:shadow-indigo-500/30 transition-all active:scale-95 group relative overflow-hidden">
                                <div className="absolute right-[-10px] bottom-[-20px] opacity-20"><BookOpen size={100} /></div>
                                <div className="relative z-10 flex items-center gap-4">
                                    <div className="p-3 bg-white/20 rounded-2xl backdrop-blur-sm"><PenTool size={24}/></div>
                                    <div>
                                        <h3 className="font-bold text-lg">Materi Mingguan</h3>
                                        <p className="text-indigo-100 text-xs font-medium opacity-90">Klik untuk buat tema & ayat baru</p>
                                    </div>
                                </div>
                            </div>
                            <div onClick={() => setIsSchedModalOpen(true)} className="glass-card p-5 rounded-3xl bg-gradient-to-r from-blue-500 to-cyan-500 text-white cursor-pointer hover:shadow-xl hover:shadow-blue-500/30 transition-all active:scale-95 group relative overflow-hidden">
                                <div className="absolute right-[-10px] bottom-[-20px] opacity-20"><CalendarDays size={100} /></div>
                                <div className="relative z-10 flex items-center gap-4">
                                    <div className="p-3 bg-white/20 rounded-2xl backdrop-blur-sm"><Clock size={24}/></div>
                                    <div>
                                        <h3 className="font-bold text-lg">Kelola Jadwal</h3>
                                        <p className="text-blue-100 text-xs font-medium opacity-90">Atur kegiatan kelas anda</p>
                                    </div>
                                </div>
                            </div>
                        </div>
                    )}

                    <div className="grid grid-cols-2 md:grid-cols-4 gap-4 mb-6">
                        <div className="glass-card p-5 rounded-3xl relative overflow-hidden group">
                            <div className="absolute right-[-20px] top-[-20px] w-24 h-24 bg-indigo-100 rounded-full opacity-50 group-hover:scale-110 transition-transform"></div>
                            <p className="text-slate-500 font-bold text-xs uppercase tracking-wider mb-2">Total Hadir</p>
                            <h3 className="text-4xl font-extrabold text-indigo-600">{att.length}</h3>
                            <p className="text-xs text-indigo-400 font-medium mt-1">Jiwat</p>
                        </div>
                        <div className="glass-card p-5 rounded-3xl relative overflow-hidden group">
                            <div className="absolute right-[-20px] top-[-20px] w-24 h-24 bg-pink-100 rounded-full opacity-50 group-hover:scale-110 transition-transform"></div>
                            <p className="text-slate-500 font-bold text-xs uppercase tracking-wider mb-2">Kelas Terbanyak</p>
                            <h3 className="text-xl font-extrabold text-pink-600 leading-tight">
                                {stats.sort((a,b) => b.value - a.value)[0]?.name.replace('Kelas ','') || '-'}
                            </h3>
                            <p className="text-xs text-pink-400 font-medium mt-1">Dominasi</p>
                        </div>
                    </div>

                    <div className="glass-card p-6 rounded-[2rem] mb-6">
                        <h3 className="font-bold text-slate-700 mb-6 flex items-center gap-2"><span className="w-2 h-6 bg-indigo-500 rounded-full"></span>Distribusi Kelas</h3>
                        <div className="h-64 w-full">
                            {stats.length > 0 ? (
                                <ResponsiveContainer>
                                    <PieChart>
                                        <Pie data={stats} innerRadius={60} outerRadius={80} paddingAngle={5} dataKey="value">
                                            {stats.map((_, i) => <Cell key={i} fill={COLORS[i % COLORS.length]} strokeWidth={0} />)}
                                        </Pie>
                                        <Tooltip contentStyle={{borderRadius: '12px', border: 'none', boxShadow: '0 10px 30px rgba(0,0,0,0.1)'}} />
                                    </PieChart>
                                </ResponsiveContainer>
                            ) : (
                                <div className="h-full flex flex-col items-center justify-center text-slate-400 opacity-60"><BarChart3 size={48} className="mb-2"/><p className="font-medium">Belum ada data</p></div>
                            )}
                        </div>
                    </div>

                    <div className="space-y-4 grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-4">
                        <h3 className="font-bold text-slate-700 px-2 col-span-full">Baru Hadir</h3>
                        {att.map((r, i) => (
                            <div key={i} className="glass-card p-4 rounded-2xl flex items-center justify-between animate-pop" style={{animationDelay: `${i*100}ms`}}>
                                <div className="flex items-center gap-4">
                                    <Avatar name={r.userName} seed={r.avatarSeed} style={r.avatarStyle} size="sm" />
                                    <div>
                                        <p className="font-bold text-slate-800 text-sm">{r.userName}</p>
                                        <p className="text-xs text-slate-500 font-semibold">{r.className}</p>
                                    </div>
                                </div>
                                <span className="bg-indigo-50 text-indigo-600 px-3 py-1 rounded-full text-[10px] font-bold">{new Date(r.timestamp).toLocaleTimeString([], {hour:'2-digit', minute:'2-digit'})}</span>
                            </div>
                        ))}
                        {att.length === 0 && <p className="text-center text-slate-400 py-8 text-sm col-span-full">Menunggu scan pertama...</p>}
                    </div>

                    {isMatModalOpen && <MaterialModal user={user} onClose={() => setIsMatModalOpen(false)} />}
                    {isSchedModalOpen && <ScheduleManagerModal user={user} onClose={() => setIsSchedModalOpen(false)} />}
                </div>
            );
        };
        const Scanner = ({ user }) => {
            const [status, setStatus] = useState({ type: 'idle', msg: '' });
            const [manual, setManual] = useState(false);
            const [txt, setTxt] = useState('');
            const ref = useRef(null);
            
            const onScan = (code) => {
                if (status.type !== 'idle') return;
                try {
                    if(ref.current && ref.current.getState() === 2) {
                        ref.current.pause();
                    }
                } catch(e) { console.log("Pause error:", e); }

                const users = DB.get(STORAGE.USERS, DEFAULT_USERS);
                const u = users.find(x => x.qrCode === code || x.id === code || x.name.toLowerCase() === code.toLowerCase());
                
                if (!u) {
                    setStatus({ type: 'err', msg: 'Data Tidak Ditemukan' });
                } else {
                    let isAllowed = false;

                    if (user.role === 'ADMIN') {
                        isAllowed = true;
                    } else if (user.role === 'TEACHER') {
                        if (u.role === 'STUDENT' && u.className === user.className) {
                            isAllowed = true;
                        } else if (u.role === 'TEACHER') {
                             setStatus({ type: 'err', msg: 'Hanya Admin yang bisa scan Guru.' });
                             setTimeout(() => { setStatus({ type: 'idle', msg: '' }); try { if(ref.current && ref.current.getState() === 3) ref.current.resume(); } catch(e){} }, 2000);
                             return;
                        } else {
                            setStatus({ type: 'err', msg: 'Siswa beda kelas / Akses ditolak' });
                             setTimeout(() => { setStatus({ type: 'idle', msg: '' }); try { if(ref.current && ref.current.getState() === 3) ref.current.resume(); } catch(e){} }, 2000);
                             return;
                        }
                    } else {
                         isAllowed = false;
                    }

                    if (isAllowed) {
                        const ok = DB.att.add({
                            id: Date.now(), userId: u.id, userName: u.name, className: u.className || '-', role: u.role,
                            // FIX: GUNAKAN getLocalDate() AGAR TERSIMPAN TANGGAL LOKAL (WIB)
                            date: getLocalDate(), 
                            timestamp: new Date().toISOString(),
                            avatarSeed: u.avatarSeed,
                            avatarStyle: u.avatarStyle || 'avataaars'
                        });
                        if (ok) DB.activities.add(user.name, `Memindai kehadiran ${u.name} (${u.role})`);
                        setStatus(ok ? { type: 'ok', msg: `Berhasil: ${u.name}` } : { type: 'err', msg: 'Sudah Absen Hari Ini' });
                    }
                }
                
                setTimeout(() => { 
                    setStatus({ type: 'idle', msg: '' }); 
                    try { 
                        if(ref.current && ref.current.getState() === 3) {
                            ref.current.resume();
                        }
                    } catch(e) { console.log("Resume error:", e); }
                }, 2000);
            };

            useEffect(() => {
                if(manual) return;
                if (ref.current) {
                    ref.current.stop().then(() => { ref.current.clear(); }).catch(() => {});
                }
                const init = async () => {
                    try {
                        const devs = await Html5Qrcode.getCameras();
                        if(devs && devs.length) {
                            const scanner = new Html5Qrcode("reader");
                            ref.current = scanner;
                            await scanner.start({ facingMode: "environment" }, { fps: 10, qrbox: 250 }, onScan);
                        }
                    } catch { setManual(true); }
                };
                const timer = setTimeout(init, 500);
                return () => { 
                    clearTimeout(timer);
                    if(ref.current) {
                        try {
                            ref.current.stop().then(() => ref.current.clear()).catch(()=>{});
                        } catch (e) {}
                    }
                };
            }, [manual]);

            return (
                <div className="p-6 pb-40 animate-slide-up min-h-full flex flex-col max-w-lg mx-auto">
                    <div className="text-center mb-6">
                        <h2 className="text-2xl font-black text-slate-800 tracking-tight">Scanner Presensi</h2>
                        {user.role === 'TEACHER' ? (
                            <div className="inline-block mt-2 px-3 py-1 bg-indigo-50 border border-indigo-100 rounded-full">
                                <p className="text-indigo-600 text-xs font-bold flex items-center gap-1">
                                    <ShieldCheck size={12}/> Mode Guru: {user.className}
                                </p>
                            </div>
                        ) : (
                            <p className="text-slate-500 text-sm font-medium">Mode Admin: Scan Guru & Siswa</p>
                        )}
                    </div>
                    <div className="flex flex-col gap-6 w-full">
                        <div className="glass-panel p-3 rounded-[2.5rem] shadow-2xl shadow-indigo-200/50 border-4 border-white/50 relative overflow-hidden bg-slate-900 group z-10">
                            <div className="relative w-full aspect-[3/4] sm:aspect-square rounded-[2rem] overflow-hidden flex items-center justify-center bg-black/20">
                                {manual ? (
                                    <div className="w-full px-6 text-center relative z-10 animate-pop">
                                        <div className="w-16 h-16 bg-white/10 rounded-full flex items-center justify-center mx-auto mb-4 backdrop-blur-md border border-white/20">
                                            <PenTool size={28} className="text-white"/>
                                        </div>
                                        <p className="text-white/60 text-xs font-medium mb-4">Mode Input Manual</p>
                                        <input 
                                            value={txt} 
                                            onChange={e => setTxt(e.target.value)} 
                                            placeholder="Ketik ID / Nama" 
                                            className="w-full p-4 rounded-2xl bg-white/10 border border-white/20 text-white font-bold text-center mb-4 placeholder-white/40 focus:bg-white/20 focus:border-white/50 outline-none transition-all backdrop-blur-sm" 
                                        />
                                        <Button onClick={() => { onScan(txt); setTxt(''); }} className="bg-white text-indigo-900 hover:bg-indigo-50 w-full py-3 text-sm">
                                            Proses Absen
                                        </Button>
                                    </div>
                                ) : (
                                    <>
                                        <div id="reader" className="w-full h-full opacity-90 object-cover absolute inset-0"></div>
                                        <div className="absolute inset-0 flex items-center justify-center pointer-events-none">
                                            <div className="w-56 h-56 relative">
                                                <div className="absolute top-0 left-0 w-10 h-10 border-l-4 border-t-4 border-white/80 rounded-tl-3xl"></div>
                                                <div className="absolute top-0 right-0 w-10 h-10 border-r-4 border-t-4 border-white/80 rounded-tr-3xl"></div>
                                                <div className="absolute bottom-0 left-0 w-10 h-10 border-l-4 border-b-4 border-white/80 rounded-bl-3xl"></div>
                                                <div className="absolute bottom-0 right-0 w-10 h-10 border-r-4 border-b-4 border-white/80 rounded-br-3xl"></div>
                                                <div className="absolute inset-x-0 top-1/2 h-0.5 bg-red-500/50 shadow-[0_0_10px_rgba(239,68,68,0.8)] animate-scan"></div>
                                            </div>
                                        </div>
                                        <div className="absolute bottom-4 left-0 right-0 text-center">
                                            <span className="bg-black/40 backdrop-blur-md text-white/80 text-[10px] px-3 py-1 rounded-full border border-white/10">Scanning...</span>
                                        </div>
                                    </>
                                )}

                                {status.type !== 'idle' && (
                                    <div className={`absolute inset-0 z-50 flex items-center justify-center bg-black/60 backdrop-blur-sm transition-all duration-300`}>
                                        <div className={`p-6 rounded-3xl shadow-2xl text-center transform scale-110 animate-pop border-4 ${
                                            status.type === 'ok' ? 'bg-white border-emerald-400' : 'bg-white border-rose-400'
                                        }`}>
                                            <div className={`w-16 h-16 rounded-full flex items-center justify-center mx-auto mb-3 ${
                                                status.type === 'ok' ? 'bg-emerald-100 text-emerald-600' : 'bg-rose-100 text-rose-600'
                                            }`}>
                                                {status.type === 'ok' ? <CheckCircle size={32}/> : <AlertCircle size={32}/>}
                                            </div>
                                            <h4 className={`text-lg font-black mb-1 ${status.type === 'ok' ? 'text-emerald-700' : 'text-rose-700'}`}>
                                                {status.type === 'ok' ? 'Berhasil!' : 'Gagal!'}
                                            </h4>
                                            <p className="text-slate-600 text-xs font-bold px-4">{status.msg}</p>
                                        </div>
                                    </div>
                                )}
                            </div>
                        </div>

                        <div className="z-20">
                            <button 
                                onClick={() => setManual(!manual)} 
                                className={`w-full py-4 rounded-2xl font-bold text-sm transition-all flex items-center justify-center gap-2 border shadow-lg active:scale-95 ${
                                    manual 
                                    ? 'bg-slate-100 text-slate-600 border-slate-200 hover:bg-slate-200' 
                                    : 'bg-white text-indigo-600 border-white hover:bg-indigo-50'
                                }`}
                            >
                                {manual ? <Camera size={18} /> : <PenTool size={18} />}
                                {manual ? 'Kembali ke Kamera' : 'Input Manual ID'}
                            </button>
                        </div>
                    </div>
                </div>
            );
        };

        const StudentDashboard = ({ user }) => {
            const [tab, setTab] = useState('card');
            const [history, setHistory] = useState([]);
            const [materials, setMaterials] = useState([]);
            const [schedules, setSchedules] = useState([]);
            const [aiDevotional, setAiDevotional] = useState(null);
            const [loadingDevo, setLoadingDevo] = useState(false);
            
            // Menggunakan onSnapshot juga untuk Siswa agar melihat update realtime (Jadwal/Materi/History)
            useEffect(() => {
                // Listener Attendance
                if (!auth.currentUser) return; // Guard
                const unsubAtt = onSnapshot(getCollectionRef('attendance'), (snap) => {
                    const data = snap.docs.map(d => d.data());
                    const myAtt = data.filter(a => a.userId === user.id).sort((a,b) => new Date(b.timestamp) - new Date(a.timestamp));
                    setHistory(myAtt);
                }, (e) => console.error(e));
                
                // Listener Materials
                const unsubMat = onSnapshot(getCollectionRef('materials'), (snap) => {
                    const data = snap.docs.map(d => d.data());
                    const myMat = data.filter(m => m.className === user.className).sort((a,b) => new Date(b.createdAt) - new Date(a.createdAt));
                    setMaterials(myMat);
                }, (e) => console.error(e));

                // Listener Schedules
                const unsubSched = onSnapshot(getCollectionRef('schedules'), (snap) => {
                    const data = snap.docs.map(d => d.data());
                    const mySched = data.filter(s => s.className === user.className || s.className === 'ALL');
                    setSchedules(mySched);
                }, (e) => console.error(e));

                return () => { if(unsubAtt) unsubAtt(); if(unsubMat) unsubMat(); if(unsubSched) unsubSched(); };
            }, [user]);

            const generateDevotional = async () => {
                setLoadingDevo(true);
                try {
                    const prompt = "Berikan satu renungan sangat singkat (1 kalimat) dan motivasi untuk anak sekolah minggu yang ceria. Format JSON: { \"title\": \"Judul Ceria\", \"content\": \"Isi Renungan\" }";
                    const res = await GeminiService.call(prompt);
                    if(res) setAiDevotional(res);
                } catch(e) { console.error(e); } finally { setLoadingDevo(false); }
            };
            const verse = useMemo(() => {
                if(materials.length > 0) return `${materials[0].verse}`;
                return MOCK_VERSES[Math.floor(Math.random()*MOCK_VERSES.length)];
            }, [materials]);
            const theme = materials.length > 0 ? materials[0].theme : "Sekolah Minggu GKPS";
            return (
                <div className="p-6 h-full flex flex-col pb-24 max-w-md mx-auto animate-slide-up">
                    <div className="flex justify-between items-center mb-6">
                        <div>
                            <h2 className="text-xl font-bold text-slate-800">Halo, {user.name.split(' ')[0]}! 👋</h2>
                            <p className="text-xs text-slate-500 font-medium">Selamat datang di {user.className}</p>
                        </div>
                        <button 
                            onClick={generateDevotional}
                            className="bg-gradient-to-tr from-yellow-400 to-orange-500 text-white p-2 rounded-xl shadow-lg hover:scale-105 transition-transform"
                            title="Renungan Harian AI"
                        >
                            {loadingDevo ? <RefreshCw size={20} className="animate-spin"/> : <Sparkles size={20}/>}
                        </button>
                    </div>

                    {aiDevotional && (
                        <div className="mb-6 bg-gradient-to-r from-yellow-50 to-orange-50 p-4 rounded-2xl border border-orange-100 shadow-sm animate-pop relative overflow-hidden">
                            <div className="absolute top-0 right-0 w-16 h-16 bg-yellow-200 rounded-full blur-2xl opacity-50 -mr-4 -mt-4"></div>
                            <div className="relative z-10">
                                <h4 className="font-bold text-orange-600 text-sm flex items-center gap-2 mb-1">
                                    <Sparkles size={12}/> {aiDevotional.title}
                                </h4>
                                <p className="text-xs text-slate-700 italic">"{aiDevotional.content}"</p>
                            </div>
                            <button onClick={()=>setAiDevotional(null)} className="absolute top-2 right-2 text-orange-300 hover:text-orange-500"><X size={14}/></button>
                        </div>
                    )}
                    
                    <div className="flex bg-white/50 p-1 rounded-2xl mb-6 backdrop-blur-sm shadow-sm border border-white/60 overflow-x-auto no-scrollbar">
                        {['card', 'history', 'materials', 'schedule'].map(t => (
                            <button key={t} onClick={() => setTab(t)}
                                className={`flex-1 min-w-[70px] py-2.5 text-[11px] font-bold rounded-xl transition-all whitespace-nowrap ${
                                    tab === t ? 'bg-white text-indigo-600 shadow-md scale-105' : 'text-slate-500 hover:text-slate-700'
                                }`}>
                                {t === 'card' ? 'Kartu' : t === 'history' ? 'Riwayat' : t === 'materials' ? 'Materi' : 'Jadwal'}
                            </button>
                        ))}
                    </div>

                    <div className="flex-1 overflow-y-auto no-scrollbar">
                        {tab === 'card' && (
                            <div className="relative w-full perspective group animate-pop">
                                <div className="absolute inset-0 bg-gradient-to-tr from-indigo-500 to-pink-500 rounded-[2.5rem] blur-xl opacity-40 group-hover:opacity-60 transition-opacity"></div>
                                <div className="relative bg-white/90 backdrop-blur-xl rounded-[2.5rem] overflow-hidden shadow-2xl border border-white/50">
                                    <div className="h-32 bg-gradient-to-r from-indigo-600 via-purple-600 to-pink-500 p-6 relative">
                                        <div className="absolute inset-0 bg-[url('https://www.transparenttextures.com/patterns/cubes.png')] opacity-20 mix-blend-overlay"></div>
                                        <div className="flex justify-between items-start relative z-10 text-white">
                                            <h1 className="font-extrabold tracking-tight">GKPS CARD</h1>
                                            <ShieldCheck size={24} className="opacity-80"/>
                                        </div>
                                    </div>
                                    <div className="px-6 pb-8 flex flex-col items-center -mt-16 relative z-10">
                                        <Avatar name={user.name} seed={user.avatarSeed} style={user.avatarStyle} size="xl" className="border-4 border-white mb-4" />
                                        <h2 className="text-2xl font-black text-slate-800 text-center mb-1 leading-tight">{user.name}</h2>
                                        <span className="bg-indigo-50 text-indigo-600 px-4 py-1 rounded-full text-xs font-bold uppercase tracking-wider mb-6 border border-indigo-100">{user.className}</span>
                                        <div className="p-4 bg-white rounded-3xl border-2 border-dashed border-slate-200 shadow-inner mb-4 group-hover:border-indigo-300 transition-colors">
                                            <QRCode value={user.qrCode} size={160} />
                                        </div>
                                        <p className="font-mono text-xs text-slate-400 font-bold tracking-widest">{user.qrCode}</p>
                                    </div>
                                    <div className="bg-slate-50 p-6 border-t border-slate-100">
                                        <p className="text-center text-xs font-bold text-indigo-600 uppercase tracking-wider mb-1">{theme}</p>
                                        <p className="text-center text-sm font-medium text-slate-600 italic">"{verse}"</p>
                                    </div>
                                </div>
                            </div>
                        )}

                        {tab === 'history' && (
                            <div className="space-y-4 animate-pop">
                                <h3 className="font-bold text-slate-700 mb-2 flex items-center gap-2">
                                    <Clock size={18} className="text-indigo-500"/> Riwayat Kehadiran
                                </h3>
                                {history.length === 0 ? (
                                    <div className="text-center py-10 text-slate-400 text-sm">Belum ada riwayat kehadiran.</div>
                                ) : (
                                    history.map((h, i) => (
                                        <div key={h.id} className="glass-card p-4 rounded-2xl flex justify-between items-center border-l-4 border-l-emerald-500">
                                            <div>
                                                <p className="font-bold text-slate-800 text-sm">{new Date(h.date).toLocaleDateString('id-ID', {weekday: 'long', year: 'numeric', month: 'long', day: 'numeric'})}</p>
                                                <p className="text-xs text-slate-500">Hadir di kelas {h.className}</p>
                                            </div>
                                            <span className="bg-emerald-50 text-emerald-600 px-3 py-1 rounded-full text-xs font-bold font-mono">
                                                {new Date(h.timestamp).toLocaleTimeString([], {hour: '2-digit', minute:'2-digit'})}
                                            </span>
                                        </div>
                                    ))
                                )}
                            </div>
                        )}

                        {tab === 'materials' && (
                            <div className="space-y-4 animate-pop">
                                <h3 className="font-bold text-slate-700 mb-2 flex items-center gap-2">
                                    <BookOpen size={18} className="text-indigo-500"/> Materi Pembelajaran
                                </h3>
                                {materials.length === 0 ? (
                                    <div className="text-center py-10 text-slate-400 text-sm">Belum ada materi dari guru.</div>
                                ) : (
                                    materials.map((m, i) => (
                                        <div key={m.id} className="glass-card p-5 rounded-2xl relative overflow-hidden">
                                            <div className="absolute top-0 left-0 w-1 h-full bg-gradient-to-b from-indigo-500 to-purple-500"></div>
                                            <div className="mb-3">
                                                <span className="text-[10px] font-bold text-indigo-400 uppercase tracking-wider bg-indigo-50 px-2 py-1 rounded-md mb-2 inline-block">
                                                    {new Date(m.createdAt).toLocaleDateString()}
                                                </span>
                                                <h4 className="text-lg font-extrabold text-slate-800 leading-tight">{m.theme}</h4>
                                                <p className="text-xs text-slate-500 mt-1">Oleh: {m.teacherName}</p>
                                            </div>
                                            <div className="bg-slate-50 p-3 rounded-xl border border-slate-100">
                                                <p className="text-sm font-medium text-slate-600 italic leading-relaxed">"{m.verse}"</p>
                                            </div>
                                        </div>
                                    ))
                                )}
                            </div>
                        )}

                        {tab === 'schedule' && (
                            <div className="space-y-4 animate-pop">
                                <h3 className="font-bold text-slate-700 mb-2 flex items-center gap-2">
                                    <CalendarDays size={18} className="text-indigo-500"/> Jadwal {user.className}
                                </h3>
                                {schedules.length === 0 ? (
                                    <div className="text-center py-10 text-slate-400 text-sm">Belum ada jadwal untuk kelas ini.</div>
                                ) : (
                                    <div className="space-y-4">
                                        {schedules.map((s, i) => (
                                            <div key={s.id} className="glass-card p-0 rounded-3xl overflow-hidden shadow-sm hover:shadow-md transition-all border border-white/60">
                                                <div className="bg-gradient-to-r from-indigo-50 to-purple-50 p-4 border-b border-indigo-100 flex justify-between items-center">
                                                    <div>
                                                        <h4 className="font-extrabold text-slate-800 text-sm">{s.activity}</h4>
                                                        <p className="text-xs text-indigo-500 font-bold uppercase tracking-wider mt-0.5">{formatDateIndo(s.date)}</p>
                                                    </div>
                                                    <span className="text-[10px] font-bold bg-white text-indigo-600 px-2 py-1 rounded-lg border border-indigo-100 shadow-sm">
                                                        {s.status === 'upcoming' ? 'Akan Datang' : 'Selesai'}
                                                    </span>
                                                </div>
                                                <div className="p-4 space-y-3">
                                                    <div className="flex items-center gap-3">
                                                        <div className="w-8 h-8 rounded-full bg-slate-50 flex items-center justify-center text-indigo-500">
                                                            <BookOpen size={16} />
                                                        </div>
                                                        <div>
                                                            <p className="text-[10px] text-slate-400 font-bold uppercase">Tema</p>
                                                            <p className="text-xs font-bold text-slate-700">{s.theme}</p>
                                                        </div>
                                                    </div>
                                                    <div className="grid grid-cols-2 gap-2">
                                                        <div className="flex items-center gap-2">
                                                            <Clock size={14} className="text-slate-400"/>
                                                            <span className="text-xs font-medium text-slate-600">{s.time}</span>
                                                        </div>
                                                        <div className="flex items-center gap-2">
                                                            <MapPin size={14} className="text-slate-400"/>
                                                            <span className="text-xs font-medium text-slate-600">{s.location}</span>
                                                        </div>
                                                    </div>
                                                    <div className="flex items-center gap-2 pt-2 border-t border-slate-50">
                                                        <User size={14} className="text-slate-400"/>
                                                        <span className="text-xs text-slate-500">Pengajar: <b>{s.speaker}</b></span>
                                                    </div>
                                                </div>
                                            </div>
                                        ))}
                                    </div>
                                )}
                            </div>
                        )}
                    </div>
                </div>
            );
        };

        const MainApp = ({ user, onLogout, onUpdateUser }) => {
            const nav = useNavigate();
            const loc = useLocation();
            const [isProfileOpen, setIsProfileOpen] = useState(false);
            const [isNotifOpen, setIsNotifOpen] = useState(false);
            const [hasNewNotif, setHasNewNotif] = useState(false);
            const menus = [
                { path: '/', icon: LayoutDashboard, label: 'Home', roles: ['ADMIN', 'TEACHER'] },
                { path: '/scan', icon: QrCode, label: 'Scan', roles: ['ADMIN', 'TEACHER'] },
                { path: '/', icon: CreditCard, label: 'Kartu', roles: ['STUDENT'] },
                { path: '/users', icon: Users, label: 'Users', roles: ['ADMIN'] },
            ];
            const myMenus = menus.filter(m => m.roles.includes(user.role));

            useEffect(() => {
                if (user.role === 'STUDENT' && loc.pathname !== '/') {
                    nav('/', { replace: true });
                }
                if (user.role === 'TEACHER' && loc.pathname === '/users') {
                    nav('/', { replace: true });
                }
            }, [user, loc.pathname, nav]);
            
            // Listen notif realtime
            useEffect(() => {
                if (!auth.currentUser) return; // Guard
                const unsubNotif = onSnapshot(getCollectionRef('notifications'), (snap) => {
                    const data = snap.docs.map(d => d.data());
                    localStorage.setItem(STORAGE.NOTIFICATIONS, JSON.stringify(data));
                    
                    if (data.length > 0) {
                        const lastNotif = data.sort((a,b)=> new Date(b.timestamp) - new Date(a.timestamp))[0];
                        const today = new Date();
                        if(new Date(lastNotif.timestamp).toDateString() === today.toDateString() && isNotifVisible(lastNotif)) {
                             setHasNewNotif(true);
                        }
                    }
                }, (e) => console.error(e));
                return () => { if(unsubNotif) unsubNotif(); };
            }, []);
            
            return (
                <div className="h-screen flex flex-col relative w-full md:max-w-7xl mx-auto bg-white/30 shadow-2xl overflow-hidden border-x border-white/40">
                    <Background />
                    <div className="glass-nav px-6 py-4 flex justify-between items-center sticky top-0 z-50">
                        <div className="flex items-center gap-3">
                            <Avatar name={user.name} seed={user.avatarSeed} style={user.avatarStyle} onClick={() => setIsProfileOpen(true)} />
                            <div className="cursor-pointer" onClick={() => setIsProfileOpen(true)}>
                                <h3 className="font-bold text-slate-800 text-sm leading-tight">{user.name.split(' ')[0]}</h3>
                                <span className="text-[10px] font-bold text-indigo-500 bg-indigo-50 px-2 py-0.5 rounded-md">{user.role}</span>
                            </div>
                        </div>
                        <div className="flex gap-2">
                            <button onClick={() => { setIsNotifOpen(true); setHasNewNotif(false); }} className="w-10 h-10 rounded-full bg-white flex items-center justify-center text-slate-400 hover:text-indigo-500 transition-colors relative">
                                <Bell size={18} />
                                {hasNewNotif && <span className="absolute top-2 right-2 w-2.5 h-2.5 bg-red-500 rounded-full border-2 border-white"></span>}
                            </button>
                            <button onClick={onLogout} className="w-10 h-10 rounded-full bg-slate-50 flex items-center justify-center text-slate-400 hover:bg-red-50 hover:text-red-500 transition-colors"><LogOut size={18} /></button>
                        </div>
                    </div>
                    <div className="flex-1 overflow-y-auto z-0">
                        <Routes>
                            <Route path="/" element={user.role === 'STUDENT' ? <StudentDashboard user={user}/> : <Dashboard user={user}/>} />
                            {user.role !== 'STUDENT' && <Route path="/scan" element={<Scanner user={user} />} />}
                            {user.role === 'ADMIN' && <Route path="/users" element={<UserManagement />} />}
                            <Route path="*" element={<div className="p-10 text-center text-slate-500">Halaman tidak ditemukan atau akses ditolak.</div>} />
                        </Routes>
                    </div>
                    {user.role !== 'STUDENT' && (
                        <div className="absolute bottom-6 left-0 right-0 z-50 flex justify-center pointer-events-none">
                            <div className="glass-nav rounded-[2rem] p-2 flex justify-between shadow-2xl shadow-indigo-500/10 w-[90%] max-w-md pointer-events-auto">
                                {myMenus.map((m, i) => {
                                    const active = loc.pathname === m.path;
                                    return (
                                        <button key={i} onClick={() => nav(m.path)}
                                            className={`flex-1 h-14 rounded-[1.8rem] flex items-center justify-center transition-all duration-300 relative ${active ? 'text-white' : 'text-slate-400 hover:bg-slate-50'}`}>
                                            {active && <div className="absolute inset-0 bg-gradient-to-tr from-indigo-500 to-pink-500 rounded-[1.8rem] shadow-lg shadow-indigo-500/30 animate-pop -z-10"></div>}
                                            <m.icon size={22} strokeWidth={active ? 2.5 : 2} className={active ? 'scale-110' : ''} />
                                        </button>
                                    );
                                })}
                            </div>
                        </div>
                    )}
                    {isProfileOpen && <ProfileModal user={user} onClose={() => setIsProfileOpen(false)} onUpdate={onUpdateUser} />}
                    {isNotifOpen && <NotificationModal onClose={() => setIsNotifOpen(false)} />}
                </div>
            );
        };

        const App = () => {
            const [user, setUser] = useState(null);
            const [isReady, setIsReady] = useState(false);
            
            useEffect(() => {
                const initApp = async () => {
                    try {
                        // CRITICAL: Auth Flow
                        if (typeof __initial_auth_token !== 'undefined' && __initial_auth_token) {
                            await signInWithCustomToken(auth, __initial_auth_token);
                            console.log("Logged in with Custom Token");
                        } else {
                            await signInAnonymously(auth);
                            console.log("Logged in Anonymously");
                        }
                        
                        await syncFromFirestore(); 
                    } catch (e) {
                        console.error("Initialization Error:", e);
                        // Jika auth gagal karena konfigurasi (Anon belum diaktifkan), beri tahu user
                        // dan biarkan aplikasi tetap berjalan dalam mode offline
                        if (e.code === 'auth/configuration-not-found' || e.code === 'auth/admin-restricted-operation') {
                            alert("PERINGATAN: Fitur 'Anonymous Sign-in' belum diaktifkan di Firebase Console. Aplikasi berjalan dalam MODE OFFLINE (Data hanya tersimpan di browser ini dan tidak akan disinkronisasi ke server).");
                        } else if (e.code === 'auth/operation-not-allowed') {
                            alert("PERINGATAN: Operasi login tidak diizinkan. Cek setting Authentication di Firebase Console.");
                        }
                    } finally {
                        // Selalu set ready agar UI tetap muncul meski auth gagal
                        setIsReady(true);
                    }
                    
                    const s = DB.get(STORAGE.SESSION); 
                    if(s) {
                        const users = DB.get(STORAGE.USERS, DEFAULT_USERS);
                        const freshUser = users.find(u => u.id === s.id);
                        if(freshUser && freshUser.isActive !== false) {
                            setUser(freshUser || s);
                        } else {
                            localStorage.removeItem(STORAGE.SESSION);
                        }
                    } 
                };
                initApp();
            }, []);

            const login = (u) => { setUser(u); DB.set(STORAGE.SESSION, u); };
            const logout = () => { 
                setUser(null);
                localStorage.removeItem(STORAGE.SESSION);
                window.location.hash = '/'; 
            };
            const handleUpdateUser = (updatedUser) => {
                const success = DB.users.update(updatedUser);
                if (success) { setUser(updatedUser); DB.set(STORAGE.SESSION, updatedUser); }
            };
            
            if (!isReady) return <LoadingScreen />;
            if (!user) return <LoginScreen onLogin={login} />;
            return <HashRouter><MainApp user={user} onLogout={logout} onUpdateUser={handleUpdateUser} /></HashRouter>;
        };

        createRoot(document.getElementById('root')).render(<App />);
    </script>
</body>
</html>
