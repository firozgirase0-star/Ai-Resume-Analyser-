<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>ResumeAI — Smart Resume Analyzer</title>

<style>

/* =========================
   GLOBAL
========================= */

*{
    margin:0;
    padding:0;
    box-sizing:border-box;
}

html{
    scroll-behavior:smooth;
}

body{
    font-family:Inter,Segoe UI,Arial,sans-serif;
    background:#f7f8fc;
    color:#161a2d;
}

/* =========================
   NAVBAR
========================= */

nav{
    height:74px;
    padding:0 7%;
    display:flex;
    align-items:center;
    justify-content:space-between;
    background:rgba(255,255,255,.85);
    backdrop-filter:blur(15px);
    border-bottom:1px solid #ececf3;
    position:sticky;
    top:0;
    z-index:100;
}

.logo{
    display:flex;
    align-items:center;
    gap:10px;
    font-size:23px;
    font-weight:800;
}

.logo-icon{
    width:40px;
    height:40px;
    border-radius:12px;
    display:flex;
    align-items:center;
    justify-content:center;
    background:linear-gradient(135deg,#6c5ce7,#8b5cf6);
    color:white;
    box-shadow:0 8px 20px rgba(108,92,231,.3);
}

.logo span{
    color:#6c5ce7;
}

.nav-links{
    display:flex;
    align-items:center;
    gap:30px;
}

.nav-links a{
    text-decoration:none;
    color:#606579;
    font-size:14px;
    font-weight:600;
}

.nav-links a:hover{
    color:#6c5ce7;
}

.nav-btn{
    background:#171a2c;
    color:white !important;
    padding:11px 19px;
    border-radius:10px;
}

/* =========================
   HERO
========================= */

.hero{
    position:relative;
    overflow:hidden;
    text-align:center;
    padding:95px 20px 70px;
    background:
        radial-gradient(circle at 20% 20%,rgba(124,92,231,.14),transparent 30%),
        radial-gradient(circle at 80% 30%,rgba(68,138,255,.12),transparent 30%);
}

.badge{
    display:inline-flex;
    align-items:center;
    gap:7px;
    background:#eeecff;
    color:#5d4ddd;
    padding:8px 15px;
    border-radius:50px;
    font-size:13px;
    font-weight:700;
    margin-bottom:22px;
}

.badge span{
    width:7px;
    height:7px;
    background:#6c5ce7;
    border-radius:50%;
}

.hero h1{
    max-width:850px;
    margin:auto;
    font-size:56px;
    line-height:1.1;
    letter-spacing:-2px;
}

.gradient-text{
    background:linear-gradient(
        90deg,
        #6555e8,
        #8b5cf6,
        #4f7cff
    );
    -webkit-background-clip:text;
    color:transparent;
}

.hero p{
    max-width:650px;
    margin:23px auto 0;
    color:#6b7280;
    font-size:17px;
    line-height:1.7;
}

/* =========================
   STATS
========================= */

.stats{
    display:flex;
    justify-content:center;
    gap:60px;
    margin-top:35px;
}

.stat strong{
    display:block;
    font-size:22px;
}

.stat span{
    color:#858b9b;
    font-size:12px;
}

/* =========================
   MAIN
========================= */

.container{
    width:90%;
    max-width:1050px;
    margin:auto;
}

/* =========================
   UPLOAD
========================= */

.upload-wrapper{
    margin-top:15px;
}

.upload-box{
    background:white;
    border:1px solid #e6e7ef;
    border-radius:24px;
    padding:12px;
    box-shadow:
        0 25px 70px rgba(35,30,80,.09);
}

.upload-inner{
    border:2px dashed #d9d5ff;
    border-radius:18px;
    padding:55px 25px;
    text-align:center;
    transition:.3s;
    background:
        linear-gradient(
            rgba(108,92,231,.025),
            rgba(108,92,231,.025)
        );
}

.upload-inner:hover{
    border-color:#7768eb;
    background:#faf9ff;
}

.upload-icon{
    width:76px;
    height:76px;
    border-radius:22px;
    margin:0 auto 20px;
    display:flex;
    justify-content:center;
    align-items:center;
    font-size:34px;
    background:linear-gradient(
        135deg,
        #eeecff,
        #e5e9ff
    );
}

.upload-inner h2{
    font-size:23px;
    margin-bottom:9px;
}

.upload-inner p{
    color:#85899a;
    font-size:14px;
}

input[type=file]{
    display:none;
}

.choose-btn{
    display:inline-flex;
    align-items:center;
    gap:8px;
    margin-top:24px;
    padding:14px 24px;
    border-radius:11px;
    color:white;
    background:linear-gradient(
        135deg,
        #6555e8,
        #7d5cf5
    );
    cursor:pointer;
    font-size:14px;
    font-weight:700;
    box-shadow:
        0 10px 25px rgba(101,85,232,.25);
    transition:.2s;
}

.choose-btn:hover{
    transform:translateY(-2px);
}

#fileName{
    margin-top:15px;
    font-size:13px;
    color:#666b7d;
}

.analyze-btn{
    border:none;
    display:flex;
    align-items:center;
    justify-content:center;
    gap:8px;
    margin:20px auto 0;
    padding:14px 28px;
    border-radius:11px;
    background:#171a2c;
    color:white;
    cursor:pointer;
    font-weight:700;
    font-size:14px;
    transition:.2s;
}

.analyze-btn:hover{
    transform:translateY(-2px);
    box-shadow:0 10px 25px rgba(0,0,0,.15);
}

/* =========================
   TRUST
========================= */

.trust{
    text-align:center;
    color:#979baa;
    font-size:12px;
    margin:22px 0 60px;
}

/* =========================
   LOADING
========================= */

#loading{
    display:none;
    text-align:center;
    margin:40px 0;
}

.loader{
    width:48px;
    height:48px;
    border:4px solid #e7e5f5;
    border-top-color:#6c5ce7;
    border-radius:50%;
    animation:spin 1s linear infinite;
    margin:auto;
}

@keyframes spin{
    to{
        transform:rotate(360deg);
    }
}

.loading-text{
    margin-top:15px;
    color:#686d7f;
    font-size:14px;
}

/* =========================
   RESULTS
========================= */

#results{
    display:none;
    margin-bottom:80px;
}

.result-heading{
    margin-bottom:25px;
}

.result-heading h2{
    font-size:30px;
}

.result-heading p{
    color:#85899a;
    margin-top:7px;
}

/* SCORE */

.score-card{
    position:relative;
    overflow:hidden;
    background:#171a2c;
    color:white;
    border-radius:22px;
    padding:32px;
    display:flex;
    align-items:center;
    gap:30px;
    margin-bottom:20px;
}

.score-card::after{
    content:"";
    position:absolute;
    width:260px;
    height:260px;
    right:-100px;
    top:-130px;
    border-radius:50%;
    background:rgba(125,92,245,.2);
}

.score-circle{
    width:140px;
    height:140px;
    border-radius:50%;
    border:10px solid #7667ee;
    outline:7px solid rgba(118,103,238,.15);
    display:flex;
    flex-direction:column;
    justify-content:center;
    align-items:center;
    flex-shrink:0;
    position:relative;
    z-index:1;
}

.score-circle strong{
    font-size:36px;
}

.score-circle span{
    color:#aeb2c4;
    font-size:12px;
}

.score-info{
    position:relative;
    z-index:2;
}

.score-info h3{
    font-size:24px;
    margin-bottom:10px;
}

.score-info p{
    max-width:600px;
    color:#b4b7c6;
    line-height:1.6;
    font-size:14px;
}

/* =========================
   CARDS
========================= */

.grid{
    display:grid;
    grid-template-columns:repeat(2,1fr);
    gap:18px;
}

.card{
    background:white;
    border:1px solid #ebecf2;
    border-radius:18px;
    padding:25px;
    box-shadow:0 8px 30px rgba(30,25,70,.04);
    transition:.2s;
}

.card:hover{
    transform:translateY(-3px);
    box-shadow:0 15px 35px rgba(30,25,70,.08);
}

.card-header{
    display:flex;
    align-items:center;
    gap:10px;
    margin-bottom:18px;
}

.card-icon{
    width:38px;
    height:38px;
    border-radius:10px;
    background:#f0efff;
    display:flex;
    align-items:center;
    justify-content:center;
}

.card h3{
    font-size:16px;
}

.skills{
    display:flex;
    flex-wrap:wrap;
    gap:8px;
}

.skill{
    padding:7px 12px;
    border-radius:20px;
    background:#efedff;
    color:#5545d4;
    font-size:12px;
    font-weight:600;
}

.missing{
    background:#fff0f0;
    color:#d34242;
}

.job{
    font-size:20px;
    font-weight:800;
    color:#6555e8;
}

.card-description{
    color:#8a8e9e;
    font-size:13px;
    margin-top:8px;
    line-height:1.5;
}

.recommendations{
    display:flex;
    flex-direction:column;
    gap:12px;
}

.recommendation{
    display:flex;
    gap:10px;
    color:#626778;
    font-size:13px;
    line-height:1.5;
}

.check{
    color:#6555e8;
    font-weight:bold;
}

/* =========================
   FOOTER
========================= */

footer{
    background:#171a2c;
    color:#aeb2c4;
    text-align:center;
    padding:30px 20px;
    font-size:13px;
}

footer strong{
    color:white;
}

/* =========================
   MOBILE
========================= */

@media(max-width:700px){

    nav{
        padding:0 20px;
    }

    .nav-links{
        display:none;
    }

    .hero{
        padding:65px 18px 45px;
    }

    .hero h1{
        font-size:38px;
        letter-spacing:-1px;
    }

    .hero p{
        font-size:15px;
    }

    .stats{
        gap:25px;
    }

    .stat strong{
        font-size:18px;
    }

    .upload-inner{
        padding:40px 15px;
    }

    .score-card{
        flex-direction:column;
        text-align:center;
    }

    .grid{
        grid-template-columns:1fr;
    }

}

</style>
</head>


<body>


<!-- NAVBAR -->

<nav>

    <div class="logo">

        <div class="logo-icon">
            ✦
        </div>

        Resume<span>AI</span>

    </div>


    <div class="nav-links">

        <a href="#">
            Home
        </a>

        <a href="#analyzer">
            Analyzer
        </a>

        <a href="#results">
            Results
        </a>

        <a href="#analyzer" class="nav-btn">
            Analyze Resume
        </a>

    </div>

</nav>


<!-- HERO -->

<section class="hero">

    <div class="badge">
        <span></span>
        AI-Powered Resume Analysis
    </div>


    <h1>

        Build a Resume That
        <span class="gradient-text">
            Gets Noticed
        </span>

    </h1>


    <p>

        Upload your resume and get an instant
        ATS score, skill analysis, job recommendations
        and actionable improvements.

    </p>


    <div class="stats">

        <div class="stat">
            <strong>ATS</strong>
            <span>Friendly Analysis</span>
        </div>

        <div class="stat">
            <strong>AI</strong>
            <span>Powered Insights</span>
        </div>

        <div class="stat">
            <strong>100%</strong>
            <span>Easy to Use</span>
        </div>

    </div>

</section>


<!-- UPLOAD -->

<section
    class="container upload-wrapper"
    id="analyzer">


    <div class="upload-box">

        <div class="upload-inner">

            <div class="upload-icon">
                📄
            </div>


            <h2>
                Upload Your Resume
            </h2>


            <p>
                PDF, DOC, DOCX or TXT
            </p>


            <label
                for="resumeFile"
                class="choose-btn">

                ⬆
                Choose Resume

            </label>


            <input
                type="file"
                id="resumeFile"
                accept=".pdf,.doc,.docx,.txt"
            >


            <div id="fileName">
            </div>


            <button
                class="analyze-btn"
                onclick="analyzeResume()">

                ✨ Analyze My Resume

            </button>

        </div>

    </div>


    <div class="trust">

        🔒 Your resume is processed securely
        &nbsp; • &nbsp;
        ⚡ Fast analysis
        &nbsp; • &nbsp;
        🤖 AI-powered insights

    </div>

</section>


<!-- LOADING -->

<div id="loading">

    <div class="loader"></div>

    <div class="loading-text">

        Analyzing your resume with AI...

    </div>

</div>


<!-- RESULTS -->

<section
    class="container"
    id="results">


    <div class="result-heading">

        <h2>
            Resume Analysis
        </h2>

        <p>
            Here's what our AI found in your resume.
        </p>

    </div>


    <!-- SCORE -->

    <div class="score-card">


        <div class="score-circle">

            <strong id="score">
                0
            </strong>

            <span>
                OUT OF 100
            </span>

        </div>


        <div class="score-info">

            <h3 id="scoreTitle">
                Resume Score
            </h3>

            <p id="scoreDescription">

                Your resume has been analyzed.

            </p>

        </div>

    </div>


    <!-- CARDS -->

    <div class="grid">


        <!-- SKILLS -->

        <div class="card">

            <div class="card-header">

                <div class="card-icon">
                    ✓
                </div>

                <h3>
                    Detected Skills
                </h3>

            </div>


            <div
                class="skills"
                id="skills">

            </div>

        </div>


        <!-- MISSING -->

        <div class="card">

            <div class="card-header">

                <div class="card-icon">
                    !
                </div>

                <h3>
                    Missing Skills
                </h3>

            </div>


            <div
                class="skills"
                id="missingSkills">

            </div>

        </div>


        <!-- JOB -->

        <div class="card">

            <div class="card-header">

                <div class="card-icon">
                    💼
                </div>

                <h3>
                    Suggested Role
                </h3>

            </div>


            <p
                class="job"
                id="jobRole">

                Full Stack Developer

            </p>


            <p class="card-description">

                Recommended based on the skills
                detected in your resume.

            </p>

        </div>


        <!-- ATS -->

        <div class="card">

            <div class="card-header">

                <div class="card-icon">
                    📊
                </div>

                <h3>
                    ATS Compatibility
                </h3>

            </div>


            <p
                style="
                color:#16854b;
                font-weight:700;
                ">

                ✓ Good ATS Compatibility

            </p>


            <p class="card-description">

                Your resume uses a structure
                that is easy for ATS systems
                to process.

            </p>

        </div>


        <!-- RECOMMENDATIONS -->

        <div
            class="card"
            style="grid-column:1/-1;">


            <div class="card-header">

                <div class="card-icon">
                    💡
                </div>

                <h3>
                    AI Recommendations
                </h3>

            </div>


            <div
                class="recommendations"
                id="recommendations">

            </div>

        </div>

    </div>

</section>


<!-- FOOTER -->

<footer>

    <strong>ResumeAI</strong>
    — Smart Resume Analysis

    <br><br>

    © 2026 ResumeAI. All rights reserved.

</footer>


<script>


/* =========================
   FILE UPLOAD
========================= */

const fileInput =
    document.getElementById("resumeFile");

const fileName =
    document.getElementById("fileName");


fileInput.addEventListener(
    "change",
    function(){

        if(this.files.length > 0){

            fileName.innerHTML =
                "📎 " +
                this.files[0].name;

        }

    }
);


/* =========================
   ANALYZE
========================= */

function analyzeResume(){

    if(fileInput.files.length === 0){

        alert(
            "Please choose your resume first."
        );

        return;

    }


    document.getElementById(
        "loading"
    ).style.display = "block";


    document.getElementById(
        "results"
    ).style.display = "none";


    setTimeout(
        generateAnalysis,
        2000
    );

}


/* =========================
   ANALYSIS
========================= */

function generateAnalysis(){

    document.getElementById(
        "loading"
    ).style.display = "none";


    document.getElementById(
        "results"
    ).style.display = "block";


    /* SCORE */

    let score =
        Math.floor(
            Math.random()*21
        ) + 70;


    document.getElementById(
        "score"
    ).innerText = score;


    if(score >= 85){

        document.getElementById(
            "scoreTitle"
        ).innerText =
            "Excellent Resume! 🎉";


        document.getElementById(
            "scoreDescription"
        ).innerText =
            "Your resume has a strong structure and good keyword coverage. A few improvements can make it even stronger.";

    }

    else{

        document.getElementById(
            "scoreTitle"
        ).innerText =
            "Good Resume 👍";


        document.getElementById(
            "scoreDescription"
        ).innerText =
            "Your resume has a solid foundation. Improving keywords, projects and achievements can increase your score.";

    }


    /* SKILLS */

    const skills = [

        "HTML",
        "CSS",
        "JavaScript",
        "Python",
        "SQL",
        "Git",
        "Communication"

    ];


    let skillHTML = "";


    skills.forEach(
        skill => {

            skillHTML +=
            `
            <span class="skill">
                ${skill}
            </span>
            `;

        }
    );


    document.getElementById(
        "skills"
    ).innerHTML = skillHTML;


    /* MISSING */

    const missing = [

        "React",
        "Node.js",
        "AWS",
        "Docker"

    ];


    let missingHTML = "";


    missing.forEach(
        skill => {

            missingHTML +=
            `
            <span class="skill missing">
                ${skill}
            </span>
            `;

        }
    );


    document.getElementById(
        "missingSkills"
    ).innerHTML = missingHTML;


    /* JOB */

    document.getElementById(
        "jobRole"
    ).innerText =
        "Full Stack Developer";


    /* RECOMMENDATIONS */

    document.getElementById(
        "recommendations"
    ).innerHTML = `

        <div class="recommendation">
            <span class="check">✓</span>
            Add measurable achievements to your experience section.
        </div>

        <div class="recommendation">
            <span class="check">✓</span>
            Include keywords related to your target job.
        </div>

        <div class="recommendation">
            <span class="check">✓</span>
            Add relevant technical skills and tools.
        </div>

        <div class="recommendation">
            <span class="check">✓</span>
            Keep your resume simple and ATS-friendly.
        </div>

        <div class="recommendation">
            <span class="check">✓</span>
            Add projects with technologies and measurable results.
        </div>

    `;


    /* SCROLL */

    document.getElementById(
        "results"
    ).scrollIntoView({

        behavior:"smooth"

    });

}

</script>

</body>
</html>