<!-- ... existing code ... -->
      .print-only {
        display: block !important;
      }
      body {
        background: #ffffff !important;
        color: #0f172a !important;
      }
      body.printing-preview > *:not(#previewModal) {
        display: none !important;
      }
      body.printing-preview #previewModal {
        position: static !important;
        display: block !important;
        background: #ffffff !important;
        padding: 0 !important;
        overflow: visible !important;
      }
      body.printing-preview #previewModalCard {
        box-shadow: none !important;
        border: none !important;
        max-width: 100% !important;
        max-height: none !important;
        overflow: visible !important;
      }
      body.printing-preview #previewScrollBody {
        overflow: visible !important;
        padding: 0 !important;
      }
      .print-card {
        box-shadow: none !important;
        border: 1px solid #cbd5e1 !important;
        break-inside: avoid;
      }
    }
  </style>
</head>
<!-- ... existing code ... -->
        <button type="button" data-tab="sekolah" class="nav-tab flex items-center gap-2 px-4 py-2.5 rounded-xl text-sm font-semibold whitespace-nowrap transition text-slate-600 hover:bg-slate-100">
          <svg class="w-4 h-4" fill="none" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24">
            <path stroke-linecap="round" stroke-linejoin="round" d="M19 21V5a2 2 0 00-2-2H7a2 2 0 00-2 2v16m14 0h2m-2 0h-5m-9 0H3m2 0h5M9 7h1m-1 4h1m4-4h1m-1 4h1m-5 10v-5a1 1 0 011-1h2a1 1 0 011 1v5m-4 0h4" />
          </svg>
          Sekolah Binaan
        </button>
        <button type="button" data-tab="rekap" class="nav-tab flex items-center gap-2 px-4 py-2.5 rounded-xl text-sm font-semibold whitespace-nowrap transition text-slate-600 hover:bg-slate-100">
          <svg class="w-4 h-4" fill="none" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24">
            <path stroke-linecap="round" stroke-linejoin="round" d="M9 17v-2m3 2v-4m3 4v-6m2 10H7a2 2 0 01-2-2V5a2 2 0 012-2h5.586a1 1 0 01.707.293l5.414 5.414a1 1 0 01.293.707V19a2 2 0 01-2 2z" />
          </svg>
          Rekap & Hasil Akhir SD
        </button>
        <button type="button" data-tab="angkakredit" class="nav-tab flex items-center gap-2 px-4 py-2.5 rounded-xl text-sm font-semibold whitespace-nowrap transition text-slate-600 hover:bg-slate-100">
<!-- ... existing code ... -->
          <div id="schoolListContainer" class="grid grid-cols-1 sm:grid-cols-2 gap-3.5">
            <!-- Diisi dinamis oleh JS -->
          </div>
        </div>
      </div>
    </section>

    <!-- ========================================================== -->
    <!-- TAB 4: REKAP KEGIATAN & HASIL AKHIR TIAP SD                -->
    <!-- ========================================================== -->
    <section id="tab-rekap" class="tab-panel hidden space-y-6">
      <!-- Bar Kontrol Filter, Preview & Cetak -->
      <div class="bg-white rounded-2xl border border-slate-200 shadow-sm p-5 sm:p-6 flex flex-col lg:flex-row lg:items-center justify-between gap-4 no-print">
        <div>
          <div class="flex items-center gap-2 flex-wrap">
            <h3 class="text-base sm:text-lg font-bold text-slate-900">Rekapitulasi Kegiatan & Hasil Akhir Tiap SD</h3>
            <span class="px-2.5 py-0.5 rounded-full text-xs font-bold bg-indigo-50 text-indigo-700 border border-indigo-200" id="rekapTpBadge">TP 2026/2027</span>
          </div>
          <p class="text-xs text-slate-500 mt-1">Menggabungkan skor penilaian 16 indikator (Lampiran I) dan realisasi jurnal kegiatan pengawasan pada masing-masing sekolah.</p>
        </div>

        <div class="flex flex-wrap items-center gap-2">
          <select id="rekapSchoolFilter" class="px-3 py-2 text-xs sm:text-sm rounded-xl border border-slate-300 bg-white font-medium text-slate-700 focus:ring-2 focus:ring-indigo-500 outline-none">
            <option value="all">Semua Sekolah Binaan</option>
          </select>
          <button type="button" onclick="exportRekapCSV()" class="px-3.5 py-2 rounded-xl bg-slate-100 hover:bg-slate-200 text-slate-700 text-xs font-semibold transition flex items-center gap-1.5">
            <svg class="w-4 h-4" fill="none" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" d="M4 16v1a3 3 0 003 3h10a3 3 0 003-3v-1m-4-4l-4 4m0 0l-4-4m4 4V4" />
            </svg>
            Unduh CSV
          </button>
          <button type="button" onclick="openPreviewModal('all')" class="px-4 py-2 rounded-xl bg-indigo-600 hover:bg-indigo-700 text-white text-xs font-semibold shadow-sm transition flex items-center gap-1.5">
            <svg class="w-4 h-4" fill="none" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" d="M15 12a3 3 0 11-6 0 3 3 0 016 0z" />
              <path stroke-linecap="round" stroke-linejoin="round" d="M2.458 12C3.732 7.943 7.523 5 12 5c4.478 0 8.268 2.943 9.542 7-1.274 4.057-5.064 7-9.542 7-4.477 0-8.268-2.943-9.542-7z" />
            </svg>
            Preview & Cetak Hasil
          </button>
        </div>
      </div>

      <!-- Kartu Ringkasan Keseluruhan -->
      <div class="grid grid-cols-2 lg:grid-cols-4 gap-4 no-print">
        <div class="bg-white rounded-2xl p-4 border border-slate-200 shadow-sm">
          <p class="text-xs font-medium text-slate-500">Sekolah Binaan Direkap</p>
          <p class="text-2xl font-extrabold text-slate-900 mt-1" id="rekapStatSchools">0</p>
        </div>
        <div class="bg-white rounded-2xl p-4 border border-slate-200 shadow-sm">
          <p class="text-xs font-medium text-indigo-600">Total Kegiatan (TP Aktif)</p>
          <p class="text-2xl font-extrabold text-indigo-700 mt-1" id="rekapStatActivities">0</p>
        </div>
        <div class="bg-white rounded-2xl p-4 border border-slate-200 shadow-sm">
          <p class="text-xs font-medium text-emerald-600">Rata-rata Skor Akhir</p>
          <p class="text-2xl font-extrabold text-emerald-700 mt-1" id="rekapStatAvg">0,00</p>
        </div>
        <div class="bg-white rounded-2xl p-4 border border-slate-200 shadow-sm">
          <p class="text-xs font-medium text-amber-600">Indikator Terisi</p>
          <p class="text-2xl font-extrabold text-amber-700 mt-1" id="rekapStatIndicators">0</p>
        </div>
      </div>

      <!-- BAGIAN 1: TABEL HASIL AKHIR TIAP SD -->
      <div class="bg-white rounded-2xl border border-slate-200 shadow-sm p-5 sm:p-6 space-y-4">
        <div class="flex flex-col sm:flex-row sm:items-center justify-between gap-2">
          <div>
            <h4 class="text-base font-bold text-slate-900">1. Hasil Akhir Pengawasan Tiap SD / Satuan Pendidikan</h4>
            <p class="text-xs text-slate-500">Rekap nilai rata-rata per pilar (1–4), nilai akhir gabungan, persentase capaian SNP, dan predikat akhir.</p>
          </div>
        </div>

        <div class="overflow-x-auto border border-slate-200 rounded-xl">
          <table class="w-full text-left text-xs">
            <thead class="bg-slate-50 text-slate-700 font-bold border-b border-slate-200">
              <tr>
                <th class="px-3.5 py-3">No</th>
                <th class="px-3.5 py-3">Nama Sekolah & KS</th>
                <th class="px-3 py-3 text-center">Indikator</th>
                <th class="px-3 py-3 text-center">Pemantauan</th>
                <th class="px-3 py-3 text-center">Penilaian</th>
                <th class="px-3 py-3 text-center">Pembinaan</th>
                <th class="px-3 py-3 text-center">Jurnal</th>
                <th class="px-3 py-3 text-center">Skor Akhir</th>
                <th class="px-3 py-3 text-center">Predikat Akhir</th>
                <th class="px-3 py-3 text-center no-print">Aksi</th>
              </tr>
            </thead>
            <tbody id="rekapFinalTableBody" class="divide-y divide-slate-100">
              <!-- Diisi dinamis oleh JS -->
            </tbody>
          </table>
        </div>
      </div>

      <!-- BAGIAN 2: REKAP MASING-MASING KEGIATAN PER SD -->
      <div class="bg-white rounded-2xl border border-slate-200 shadow-sm p-5 sm:p-6 space-y-4">
        <div>
          <h4 class="text-base font-bold text-slate-900">2. Rekap Masing-Masing Kegiatan Pengawasan per Sekolah</h4>
          <p class="text-xs text-slate-500">Rincian kegiatan per pilar (Pemantauan, Penilaian, Pembinaan), indikator dinilai, skor, dan bukti dukung untuk setiap SD.</p>
        </div>
        <div id="rekapPerSchoolContainer" class="space-y-5">
          <!-- Diisi dinamis oleh JS -->
        </div>
      </div>
    </section>

    <!-- ========================================================== -->
    <!-- TAB 5: KALKULATOR ANGKA KREDIT & SIMULASI KARIER           -->
    <!-- ========================================================== -->
    <section id="tab-angkakredit" class="tab-panel hidden space-y-6">
<!-- ... existing code ... -->
  <!-- ==================== TOAST NOTIFICATION ==================== -->
  <div id="toast" class="fixed bottom-5 right-5 z-50 hidden items-center gap-2.5 px-4 py-3 rounded-xl bg-slate-900 text-white text-xs sm:text-sm font-medium shadow-lg no-print">
    <span class="w-2 h-2 rounded-full bg-emerald-400"></span>
    <span id="toastMessage">Berhasil disimpan</span>
  </div>

  <!-- ==================== MODAL PREVIEW & CETAK HASIL ==================== -->
  <div id="previewModal" class="fixed inset-0 z-50 hidden items-center justify-center bg-slate-900/70 backdrop-blur-xs p-3 sm:p-6">
    <div id="previewModalCard" class="bg-white rounded-2xl max-w-5xl w-full max-h-[92vh] flex flex-col shadow-2xl border border-slate-200 overflow-hidden">
      <!-- Header Modal Preview (Disembunyikan saat print) -->
      <div class="px-5 py-4 border-b border-slate-200 bg-slate-900 text-white flex flex-wrap items-center justify-between gap-3 no-print">
        <div class="flex items-center gap-2.5">
          <span class="px-2.5 py-1 rounded-lg bg-indigo-500/30 text-indigo-200 text-xs font-bold border border-indigo-400/30">PREVIEW LAPORAN</span>
          <div>
            <h3 class="text-sm sm:text-base font-bold" id="previewModalTitle">Pratinjau Laporan Hasil Pengawasan</h3>
            <p class="text-[11px] text-slate-400">Periksa tampilan dokumen sebelum mencetak atau menyimpan ke PDF.</p>
          </div>
        </div>
        <div class="flex items-center gap-2">
          <button type="button" onclick="printPreviewDocument()" class="px-4 py-2 rounded-xl bg-emerald-500 hover:bg-emerald-600 text-white text-xs font-bold shadow-sm transition flex items-center gap-1.5">
            <svg class="w-4 h-4" fill="none" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" d="M17 17h2a2 2 0 002-2v-4a2 2 0 00-2-2H5a2 2 0 00-2 2v4a2 2 0 002 2h2m2 4h6a2 2 0 002-2v-4a2 2 0 00-2-2H9a2 2 0 00-2 2v4a2 2 0 002 2zm8-12V5a2 2 0 00-2-2H9a2 2 0 00-2 2v4h10z" />
            </svg>
            Cetak Hasil (Print / PDF)
          </button>
          <button type="button" id="btnClosePreview" class="p-2 rounded-xl text-slate-400 hover:bg-slate-800 hover:text-white transition" title="Tutup Preview">
            <svg class="w-5 h-5" fill="none" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" d="M6 18L18 6M6 6l12 12" />
            </svg>
          </button>
        </div>
      </div>

      <!-- Area Dokumen Siap Cetak -->
      <div id="previewScrollBody" class="p-5 sm:p-8 overflow-y-auto bg-slate-100/80 flex-1">
        <div id="printAreaContent" class="bg-white max-w-4xl mx-auto p-6 sm:p-10 rounded-xl shadow-sm border border-slate-200 text-slate-900 space-y-6">
          <!-- Diisi dinamis oleh JS -->
        </div>
      </div>
    </div>
  </div>

  <!-- ==================== JAVASCRIPT LOGIC ==================== -->
<!-- ... existing code ... -->
      schools: [
        { id: 'sch-1', name: 'SDN 1 Harapan Bangsa', level: 'SD', npsn: '20310001', principal: 'Siti Aminah, S.Pd.', priority: 'Penguatan Literasi & Numerasi' },
        { id: 'sch-2', name: 'SDN 2 Nusantara', level: 'SD', npsn: '20310045', principal: 'Ahmad Fauzi, M.Pd.', priority: 'Peningkatan Kualitas Pembelajaran' }
      ],
      // Menyimpan skor (1-4) dan bukti dukung untuk setiap indikator (16 butir)
      // Key: `${tahunPelajaran}||${schoolName}||${jenjang}||${pillar}||${idx}`
      indicatorAssessments: {
        '2026/2027||SDN 1 Harapan Bangsa||madya||pemantauan||0': {
          score: 4,
          evidence: 'Dokumen KSP & RKAS SDN 1 Harapan Bangsa 2026.pdf'
        },
        '2026/2027||SDN 1 Harapan Bangsa||madya||pemantauan||4': {
          score: 3,
          evidence: 'Rekap Rapor Pendidikan 2026 & Berita Acara Pemantauan.pdf'
        },
        '2026/2027||SDN 1 Harapan Bangsa||madya||penilaian||2': {
          score: 4,
          evidence: 'Instrumen Rekomendasi Kinerja Kepala Sekolah.pdf'
        },
        '2026/2027||SDN 1 Harapan Bangsa||madya||pembinaan||2': {
          score: 3,
          evidence: 'Daftar Hadir & Notulen Pendampingan Pembelajaran Mendalam.pdf'
        },
        '2026/2027||SDN 2 Nusantara||madya||pemantauan||1': {
          score: 3,
          evidence: 'Instrumen Pemantauan 8 SNP SDN 2 Nusantara.pdf'
        },
        '2026/2027||SDN 2 Nusantara||madya||penilaian||3': {
          score: 3,
          evidence: 'Lembar Observasi Supervisi Kelas.pdf'
        }
      },
      logs: [
        {
          id: 'log-1',
          date: new Date().toISOString().split('T')[0],
          tahunPelajaran: '2026/2027',
          schoolName: 'SDN 1 Harapan Bangsa',
          pillar: 'pemantauan',
          indicator: 'e. Pemantauan peningkatan capaian Rapor Pendidikan dengan menganalisis mutu literasi, numerasi, dan karakter siswa.',
          score: 3,
          finding: 'Capaian numerasi kelas V masih berada pada kategori sedang; pemanfaatan buku nonteks di pojok baca perlu dioptimalkan.',
          rtl: 'Menyusun jadwal pendampingan komunitas belajar guru kelas atas untuk perancangan pembelajaran numerasi kontekstual.',
          evidence: 'Berita Acara Pemantauan & Rekap Rapor Pendidikan 2026.pdf',
          status: 'Terlaksana'
        },
        {
          id: 'log-2',
          date: new Date().toISOString().split('T')[0],
          tahunPelajaran: '2026/2027',
          schoolName: 'SDN 2 Nusantara',
          pillar: 'pembinaan',
          indicator: 'c. Pembinaan akademik metode pembelajaran berkesadaran, bermakna, dan menggembirakan serta penilaian sesuai SNP untuk literasi, numerasi, dan karakter kepada Guru.',
          score: 4,
          finding: 'Guru kelas rendah telah menerapkan pembelajaran aktif berbasis proyek sederhana dengan sangat antusias.',
          rtl: 'Mendorong pengimbasan praktik baik guru SDN 2 Nusantara pada forum KKG gugus.',
          evidence: 'Foto Pendampingan & Modul Ajar Berdiferensiasi.pdf',
          status: 'Terlaksana'
        }
      ],
      akPeriods: [
<!-- ... existing code ... -->
    function renderTahunPelajaran() {
      const tp = appState.tahunPelajaran || '2026/2027';
      document.getElementById('headerTpLabel').textContent = tp;
      document.getElementById('printTp').textContent = tp;
      const rekapBadge = document.getElementById('rekapTpBadge');
      if (rekapBadge) rekapBadge.textContent = `TP ${tp}`;
      renderTupoksiList();
      renderRekapTab();
    }

    // ==================== TAB 1: ANALISIS TUPOKSI & PENILAIAN 16 INDIKATOR ====================
<!-- ... existing code ... -->
    function setIndicatorScore(pillar, idx, scoreVal) {
      const key = getAssessmentKey(pillar, idx);
      const current = appState.indicatorAssessments[key] || { score: null, evidence: '' };
      appState.indicatorAssessments[key] = { ...current, score: scoreVal };
      renderTupoksiList();
      renderRekapTab();
    }

    function setIndicatorEvidence(pillar, idx, val) {
      const key = getAssessmentKey(pillar, idx);
      const current = appState.indicatorAssessments[key] || { score: null, evidence: '' };
      appState.indicatorAssessments[key] = { ...current, evidence: val };
      updateEvidenceLinkPreview(pillar, idx, val);
      renderRekapTab();
    }
<!-- ... existing code ... -->
      const instrSel = document.getElementById('instrumenSchoolSelect');
      if (instrSel) {
        const prev = instrSel.value;
        instrSel.innerHTML = optionsHtml;
        if (prev && Array.from(instrSel.options).some(o => o.value === prev)) {
          instrSel.value = prev;
        }
      }

      const rekapSel = document.getElementById('rekapSchoolFilter');
      if (rekapSel) {
        const prevRekap = rekapSel.value;
        rekapSel.innerHTML = `<option value="all">Semua Sekolah Binaan (${appState.schools.length})</option>` + optionsHtml;
        if (prevRekap && Array.from(rekapSel.options).some(o => o.value === prevRekap)) {
          rekapSel.value = prevRekap;
        }
      }
    }
<!-- ... existing code ... -->
    function deleteLog(id) {
      appState.logs = appState.logs.filter(l => l.id !== id);
      renderLogs();
      renderRekapTab();
      showToast('Catatan pengawasan dihapus.');
    }
<!-- ... existing code ... -->
      populateSchoolSelect();
      renderTupoksiList();
      renderRekapTab();
    }

    function deleteSchool(id) {
      appState.schools = appState.schools.filter(s => s.id !== id);
      renderSchools();
      showToast('Sekolah binaan dihapus.');
    }

    // ==================== TAB 4: REKAP KEGIATAN & HASIL AKHIR TIAP SD ====================
    function calculateSchoolRecap(school) {
      const tp = appState.tahunPelajaran || '2026/2027';
      const jenjang = currentAnalysisJenjang || appState.profile.jenjang || 'madya';
      const data = TUPOKSI_DATA[jenjang];

      const pillarStats = {
        pemantauan: { sum: 0, count: 0, totalItems: data.pillars.pemantauan.items.length, items: [] },
        penilaian: { sum: 0, count: 0, totalItems: data.pillars.penilaian.items.length, items: [] },
        pembinaan: { sum: 0, count: 0, totalItems: data.pillars.pembinaan.items.length, items: [] }
      };

      let totalIndScore = 0;
      let totalIndFilled = 0;

      ['pemantauan', 'penilaian', 'pembinaan'].forEach(pKey => {
        data.pillars[pKey].items.forEach((itemText, idx) => {
          const key = `${tp}||${school.name}||${jenjang}||${pKey}||${idx}`;
          const rec = appState.indicatorAssessments[key];
          const sc = rec && rec.score ? Number(rec.score) : null;
          const ev = rec && rec.evidence ? rec.evidence.trim() : '';

          if (sc) {
            pillarStats[pKey].sum += sc;
            pillarStats[pKey].count += 1;
            totalIndScore += sc;
            totalIndFilled += 1;
          }

          if (sc || ev) {
            pillarStats[pKey].items.push({
              pillar: pKey,
              indicator: itemText,
              score: sc,
              evidence: ev
            });
          }
        });
      });

      // Filter jurnal pada sekolah & TP aktif
      const schoolLogs = appState.logs.filter(l =>
        l.schoolName === school.name &&
        (!l.tahunPelajaran || l.tahunPelajaran === tp)
      );

      const logScoreSum = schoolLogs.reduce((acc, l) => acc + (Number(l.score) || 0), 0);
      const avgLogScore = schoolLogs.length > 0 ? (logScoreSum / schoolLogs.length) : 0;
      const avgIndScore = totalIndFilled > 0 ? (totalIndScore / totalIndFilled) : 0;

      // Nilai akhir menggabungkan skor indikator (bobot 70% jika keduanya ada) & jurnal kegiatan (30%), atau salah satu jika hanya satu yang terisi
      let finalScore = 0;
      if (totalIndFilled > 0 && schoolLogs.length > 0) {
        finalScore = (avgIndScore * 0.7) + (avgLogScore * 0.3);
      } else if (totalIndFilled > 0) {
        finalScore = avgIndScore;
      } else if (schoolLogs.length > 0) {
        finalScore = avgLogScore;
      }

      const percentage = (finalScore / 4) * 100;
      let predikat = { label: 'Belum Dinilai', desc: 'Belum ada skor indikator maupun jurnal.', badge: 'bg-slate-100 text-slate-600 border-slate-200', scoreNum: 0 };

      if (finalScore > 0) {
        if (finalScore >= 3.51) {
          predikat = { ...SCORE_RUBRIC[4], scoreNum: 4 };
        } else if (finalScore >= 2.51) {
          predikat = { ...SCORE_RUBRIC[3], scoreNum: 3 };
        } else if (finalScore >= 1.51) {
          predikat = { ...SCORE_RUBRIC[2], scoreNum: 2 };
        } else {
          predikat = { ...SCORE_RUBRIC[1], scoreNum: 1 };
        }
      }

      return {
        school,
        tp,
        jenjangLabel: data.label,
        pillarStats,
        totalIndFilled,
        avgIndScore,
        schoolLogs,
        avgLogScore,
        finalScore,
        percentage,
        predikat
      };
    }

    function renderRekapTab() {
      const tbody = document.getElementById('rekapFinalTableBody');
      const perSchoolBox = document.getElementById('rekapPerSchoolContainer');
      if (!tbody || !perSchoolBox) return;

      const filterVal = document.getElementById('rekapSchoolFilter')?.value || 'all';
      const targetSchools = filterVal === 'all'
        ? appState.schools
        : appState.schools.filter(s => s.name === filterVal);

      const recaps = targetSchools.map(s => calculateSchoolRecap(s));

      // Update statistik ringkas
      document.getElementById('rekapStatSchools').textContent = recaps.length;
      const totalActs = recaps.reduce((sum, r) => sum + r.schoolLogs.length, 0);
      const totalInds = recaps.reduce((sum, r) => sum + r.totalIndFilled, 0);
      const ratedRecaps = recaps.filter(r => r.finalScore > 0);
      const overallAvg = ratedRecaps.length > 0
        ? ratedRecaps.reduce((sum, r) => sum + r.finalScore, 0) / ratedRecaps.length
        : 0;

      document.getElementById('rekapStatActivities').textContent = totalActs;
      document.getElementById('rekapStatIndicators').textContent = `${totalInds} / ${recaps.length * 16}`;
      document.getElementById('rekapStatAvg').textContent = formatNum(overallAvg);

      if (recaps.length === 0) {
        tbody.innerHTML = `<tr><td colspan="10" class="px-4 py-8 text-center text-slate-400">Belum ada data sekolah binaan. Tambahkan sekolah pada tab Sekolah Binaan.</td></tr>`;
        perSchoolBox.innerHTML = `<div class="text-center py-8 text-sm text-slate-400 border border-dashed border-slate-300 rounded-xl">Belum ada data kegiatan untuk ditampilkan.</div>`;
        return;
      }

      // 1. Render Tabel Hasil Akhir Tiap SD
      tbody.innerHTML = recaps.map((r, index) => {
        const avgP1 = r.pillarStats.pemantauan.count > 0 ? formatNum(r.pillarStats.pemantauan.sum / r.pillarStats.pemantauan.count) : '-';
        const avgP2 = r.pillarStats.penilaian.count > 0 ? formatNum(r.pillarStats.penilaian.sum / r.pillarStats.penilaian.count) : '-';
        const avgP3 = r.pillarStats.pembinaan.count > 0 ? formatNum(r.pillarStats.pembinaan.sum / r.pillarStats.pembinaan.count) : '-';

        return `
          <tr class="hover:bg-slate-50/80">
            <td class="px-3.5 py-3 font-semibold text-slate-600">${index + 1}</td>
            <td class="px-3.5 py-3">
              <p class="font-bold text-slate-900">${escapeHtml(r.school.name)}</p>
              <p class="text-[11px] text-slate-500">NPSN: ${escapeHtml(r.school.npsn || '-')} • KS: ${escapeHtml(r.school.principal)}</p>
            </td>
            <td class="px-3.5 py-3 text-center font-semibold text-slate-700">${r.totalIndFilled} / 16</td>
            <td class="px-3.5 py-3 text-center font-medium text-blue-700">${avgP1}</td>
            <td class="px-3.5 py-3 text-center font-medium text-amber-700">${avgP2}</td>
            <td class="px-3.5 py-3 text-center font-medium text-emerald-700">${avgP3}</td>
            <td class="px-3.5 py-3 text-center font-semibold text-slate-700">${r.schoolLogs.length} keg (${r.schoolLogs.length > 0 ? formatNum(r.avgLogScore) : '-'})</td>
            <td class="px-3.5 py-3 text-center">
              <span class="font-extrabold text-sm text-indigo-700">${r.finalScore > 0 ? formatNum(r.finalScore) : '-'}</span>
              ${r.finalScore > 0 ? `<span class="block text-[10px] text-slate-400">(${r.percentage.toFixed(1)}%)</span>` : ''}
            </td>
            <td class="px-3.5 py-3 text-center">
              <span class="inline-block px-2.5 py-1 rounded-lg text-[11px] font-bold border ${r.predikat.badge}">
                ${r.predikat.label}
              </span>
            </td>
            <td class="px-3.5 py-3 text-center no-print">
              <button type="button" onclick="openPreviewModal('${escapeHtml(r.school.name)}')" class="px-2.5 py-1.5 rounded-lg bg-indigo-50 hover:bg-indigo-100 text-indigo-700 font-semibold text-[11px] transition">
                Preview SD
              </button>
            </td>
          </tr>
        `;
      }).join('');

      // 2. Render Rekap Masing-Masing Kegiatan per SD
      const pillarTitles = {
        pemantauan: { label: '1. Pemantauan', badge: 'bg-blue-100 text-blue-700' },
        penilaian: { label: '2. Penilaian', badge: 'bg-amber-100 text-amber-700' },
        pembinaan: { label: '3. Pembinaan', badge: 'bg-emerald-100 text-emerald-700' }
      };

      perSchoolBox.innerHTML = recaps.map(r => {
        const logRowsHtml = r.schoolLogs.length === 0
          ? `<p class="text-xs text-slate-400 italic py-2">Belum ada catatan jurnal kegiatan pada sekolah ini untuk TP ${escapeHtml(r.tp)}.</p>`
          : `<div class="overflow-x-auto border border-slate-200 rounded-xl">
              <table class="w-full text-left text-xs">
                <thead class="bg-slate-50 text-slate-600 font-semibold border-b border-slate-200">
                  <tr>
                    <th class="px-3 py-2">Tanggal</th>
                    <th class="px-3 py-2">Pilar</th>
                    <th class="px-3 py-2">Kegiatan & Temuan</th>
                    <th class="px-3 py-2 text-center">Skor</th>
                    <th class="px-3 py-2">Bukti Dukung</th>
                  </tr>
                </thead>
                <tbody class="divide-y divide-slate-100">
                  ${r.schoolLogs.map(l => {
                    const sc = SCORE_RUBRIC[Number(l.score) || 3];
                    const pInfo = pillarTitles[l.pillar] || pillarTitles.pemantauan;
                    return `
                      <tr>
                        <td class="px-3 py-2 whitespace-nowrap text-slate-600">${escapeHtml(l.date)}</td>
                        <td class="px-3 py-2 whitespace-nowrap"><span class="px-2 py-0.5 rounded-md text-[10px] font-bold ${pInfo.badge}">${pInfo.label}</span></td>
                        <td class="px-3 py-2">
                          <p class="font-semibold text-slate-800">${escapeHtml(l.indicator)}</p>
                          <p class="text-[11px] text-slate-500 mt-0.5">Temuan: ${escapeHtml(l.finding)}</p>
                        </td>
                        <td class="px-3 py-2 text-center whitespace-nowrap">
                          <span class="px-2 py-0.5 rounded-md text-[11px] font-bold border ${sc.badge}">${l.score} (${sc.label})</span>
                        </td>
                        <td class="px-3 py-2 text-[11px] text-slate-600">${escapeHtml(l.evidence || '-')}</td>
                      </tr>
                    `;
                  }).join('')}
                </tbody>
              </table>
            </div>`;

        // Ringkasan indikator instrumen yang sudah dinilai
        const assessedItems = [
          ...r.pillarStats.pemantauan.items,
          ...r.pillarStats.penilaian.items,
          ...r.pillarStats.pembinaan.items
        ];

        const indSummaryHtml = assessedItems.length === 0
          ? `<p class="text-xs text-slate-400 italic py-2">Belum ada butir pada Instrumen 16 Indikator yang diberi skor untuk sekolah ini.</p>`
          : `<div class="grid grid-cols-1 md:grid-cols-2 gap-2.5">
              ${assessedItems.map(it => {
                const sc = it.score ? SCORE_RUBRIC[it.score] : null;
                const pInfo = pillarTitles[it.pillar];
                return `
                  <div class="p-3 rounded-xl bg-slate-50 border border-slate-200/80 text-xs space-y-1">
                    <div class="flex items-center justify-between gap-2">
                      <span class="px-2 py-0.5 rounded-md text-[10px] font-bold ${pInfo.badge}">${pInfo.label}</span>
                      ${sc ? `<span class="px-2 py-0.5 rounded-md text-[10px] font-bold border ${sc.badge}">Skor ${it.score}: ${sc.label}</span>` : ''}
                    </div>
                    <p class="font-medium text-slate-800 leading-snug">${escapeHtml(it.indicator)}</p>
                    <p class="text-[11px] text-slate-500">Bukti: ${escapeHtml(it.evidence || '-')}</p>
                  </div>
                `;
              }).join('')}
            </div>`;

        return `
          <div class="rounded-2xl border border-slate-200 p-4 sm:p-5 space-y-4 bg-slate-50/40">
            <div class="flex flex-col sm:flex-row sm:items-center justify-between gap-2 border-b border-slate-200 pb-3">
              <div>
                <div class="flex items-center gap-2">
                  <span class="px-2 py-0.5 rounded-md text-[11px] font-bold bg-indigo-100 text-indigo-700">${escapeHtml(r.school.level)}</span>
                  <h5 class="font-bold text-slate-900 text-sm sm:text-base">${escapeHtml(r.school.name)}</h5>
                </div>
                <p class="text-xs text-slate-500 mt-0.5">Kepala Sekolah: ${escapeHtml(r.school.principal)} • Prioritas: ${escapeHtml(r.school.priority)}</p>
              </div>
              <div class="flex items-center gap-2">
                <div class="text-right">
                  <p class="text-[10px] uppercase font-semibold text-slate-400">Hasil Akhir</p>
                  <p class="text-sm font-extrabold text-indigo-700">${r.finalScore > 0 ? `${formatNum(r.finalScore)} / 4,00 (${r.predikat.label})` : 'Belum Dinilai'}</p>
                </div>
                <button type="button" onclick="openPreviewModal('${escapeHtml(r.school.name)}')" class="no-print px-3 py-2 rounded-xl bg-white border border-slate-300 hover:bg-slate-100 text-slate-700 text-xs font-semibold transition">
                  Preview & Cetak
                </button>
              </div>
            </div>

            <div class="space-y-2">
              <p class="text-xs font-bold text-slate-700">A. Rekap Jurnal Kegiatan Pengawasan (${r.schoolLogs.length} Kegiatan)</p>
              ${logRowsHtml}
            </div>

            <div class="space-y-2">
              <p class="text-xs font-bold text-slate-700">B. Rekap Penilaian Instrumen 16 Indikator (${r.totalIndFilled} dari 16 Indikator Dinilai)</p>
              ${indSummaryHtml}
            </div>
          </div>
        `;
      }).join('');
    }

    function openPreviewModal(schoolFilterName = 'all') {
      const tp = appState.tahunPelajaran || '2026/2027';
      const p = appState.profile;
      const jenjangText = p.jenjang === 'muda' ? 'Ahli Muda' : p.jenjang === 'madya' ? 'Ahli Madya' : 'Ahli Utama';

      const targetSchools = schoolFilterName === 'all'
        ? appState.schools
        : appState.schools.filter(s => s.name === schoolFilterName);

      const recaps = targetSchools.map(s => calculateSchoolRecap(s));

      document.getElementById('previewModalTitle').textContent = schoolFilterName === 'all'
        ? `Pratinjau Laporan Rekap & Hasil Akhir (${recaps.length} Sekolah)`
        : `Pratinjau Laporan Hasil Pengawasan — ${schoolFilterName}`;

      const summaryRowsHtml = recaps.map((r, idx) => {
        const avgP1 = r.pillarStats.pemantauan.count > 0 ? formatNum(r.pillarStats.pemantauan.sum / r.pillarStats.pemantauan.count) : '-';
        const avgP2 = r.pillarStats.penilaian.count > 0 ? formatNum(r.pillarStats.penilaian.sum / r.pillarStats.penilaian.count) : '-';
        const avgP3 = r.pillarStats.pembinaan.count > 0 ? formatNum(r.pillarStats.pembinaan.sum / r.pillarStats.pembinaan.count) : '-';
        return `
          <tr>
            <td class="border border-slate-300 px-2.5 py-2 text-center">${idx + 1}</td>
            <td class="border border-slate-300 px-2.5 py-2">
              <strong>${escapeHtml(r.school.name)}</strong><br/>
              <span class="text-[11px] text-slate-600">KS: ${escapeHtml(r.school.principal)}</span>
            </td>
            <td class="border border-slate-300 px-2.5 py-2 text-center">${r.totalIndFilled}/16</td>
            <td class="border border-slate-300 px-2.5 py-2 text-center">${avgP1}</td>
            <td class="border border-slate-300 px-2.5 py-2 text-center">${avgP2}</td>
            <td class="border border-slate-300 px-2.5 py-2 text-center">${avgP3}</td>
            <td class="border border-slate-300 px-2.5 py-2 text-center">${r.schoolLogs.length}</td>
            <td class="border border-slate-300 px-2.5 py-2 text-center font-bold">${r.finalScore > 0 ? formatNum(r.finalScore) : '-'}</td>
            <td class="border border-slate-300 px-2.5 py-2 text-center font-bold">${r.predikat.label}</td>
          </tr>
        `;
      }).join('');

      const detailBlocksHtml = recaps.map(r => {
        const allActivities = r.schoolLogs.map((l, i) => {
          const sc = SCORE_RUBRIC[Number(l.score) || 3];
          return `
            <tr>
              <td class="border border-slate-300 px-2 py-1.5 text-center">${i + 1}</td>
              <td class="border border-slate-300 px-2 py-1.5 whitespace-nowrap">${escapeHtml(l.date)}</td>
              <td class="border border-slate-300 px-2 py-1.5 uppercase">${escapeHtml(l.pillar)}</td>
              <td class="border border-slate-300 px-2 py-1.5">
                <p class="font-semibold">${escapeHtml(l.indicator)}</p>
                <p class="text-[11px] text-slate-600">Temuan: ${escapeHtml(l.finding)} | RTL: ${escapeHtml(l.rtl)}</p>
              </td>
              <td class="border border-slate-300 px-2 py-1.5 text-center font-semibold">${l.score} (${sc.label})</td>
              <td class="border border-slate-300 px-2 py-1.5 text-[11px]">${escapeHtml(l.evidence || '-')}</td>
            </tr>
          `;
        }).join('');

        return `
          <div class="space-y-2 pt-3 break-inside-avoid">
            <h4 class="text-xs font-bold uppercase bg-slate-100 px-3 py-2 border border-slate-300">
              Rincian Kegiatan Pengawasan: ${escapeHtml(r.school.name)} (Hasil Akhir: ${r.finalScore > 0 ? `${formatNum(r.finalScore)} - ${r.predikat.label}` : 'Belum Dinilai'})
            </h4>
            ${r.schoolLogs.length > 0 ? `
              <table class="w-full border-collapse text-xs">
                <thead>
                  <tr class="bg-slate-50">
                    <th class="border border-slate-300 px-2 py-1.5 text-center w-8">No</th>
                    <th class="border border-slate-300 px-2 py-1.5">Tanggal</th>
                    <th class="border border-slate-300 px-2 py-1.5">Pilar</th>
                    <th class="border border-slate-300 px-2 py-1.5">Uraian Kegiatan, Temuan & RTL</th>
                    <th class="border border-slate-300 px-2 py-1.5 text-center">Skor</th>
                    <th class="border border-slate-300 px-2 py-1.5">Bukti Dukung</th>
                  </tr>
                </thead>
                <tbody>${allActivities}</tbody>
              </table>
            ` : `<p class="text-xs text-slate-500 italic px-2">Belum ada catatan kegiatan pada jurnal untuk sekolah ini.</p>`}
          </div>
        `;
      }).join('');

      const todayFormatted = new Date().toLocaleDateString('id-ID', { day: 'numeric', month: 'long', year: 'numeric' });

      document.getElementById('printAreaContent').innerHTML = `
        <!-- Kop Dokumen -->
        <div class="text-center border-b-2 border-slate-900 pb-4 space-y-1">
          <h2 class="text-base sm:text-lg font-extrabold uppercase tracking-wide">Laporan Rekapitulasi Kegiatan & Hasil Akhir Pengawasan Sekolah</h2>
          <p class="text-xs text-slate-600">Sesuai Permendikdasmen Nomor 28 Tahun 2026 • Tahun Pelajaran ${escapeHtml(tp)}</p>
        </div>

        <!-- Identitas Pengawas -->
        <div class="grid grid-cols-1 sm:grid-cols-2 gap-x-6 gap-y-1.5 text-xs bg-slate-50 p-4 rounded-lg border border-slate-200">
          <p><span class="text-slate-500 inline-block w-36">Nama Pengawas</span>: <strong>${escapeHtml(p.name)}</strong></p>
          <p><span class="text-slate-500 inline-block w-36">NIP</span>: <strong>${escapeHtml(p.nip || '-')}</strong></p>
          <p><span class="text-slate-500 inline-block w-36">Jenjang / Golongan</span>: Pengawas Sekolah ${jenjangText} (${escapeHtml(p.gol)})</p>
          <p><span class="text-slate-500 inline-block w-36">Instansi</span>: ${escapeHtml(p.instansi || '-')}</p>
          <p><span class="text-slate-500 inline-block w-36">Tahun Pelajaran</span>: <strong>${escapeHtml(tp)}</strong></p>
          <p><span class="text-slate-500 inline-block w-36">Tanggal Cetak</span>: ${todayFormatted}</p>
        </div>

        <!-- Tabel Hasil Akhir Tiap SD -->
        <div class="space-y-2">
          <h3 class="text-xs font-bold uppercase tracking-wider text-slate-800">I. Rekapitulasi Hasil Akhir Pengawasan Tiap Satuan Pendidikan</h3>
          <div class="overflow-x-auto">
            <table class="w-full border-collapse text-xs">
              <thead>
                <tr class="bg-slate-100">
                  <th class="border border-slate-300 px-2.5 py-2 text-center">No</th>
                  <th class="border border-slate-300 px-2.5 py-2">Nama Sekolah & Kepala Sekolah</th>
                  <th class="border border-slate-300 px-2.5 py-2 text-center">Indikator</th>
                  <th class="border border-slate-300 px-2.5 py-2 text-center">Pemantauan</th>
                  <th class="border border-slate-300 px-2.5 py-2 text-center">Penilaian</th>
                  <th class="border border-slate-300 px-2.5 py-2 text-center">Pembinaan</th>
                  <th class="border border-slate-300 px-2.5 py-2 text-center">Jurnal</th>
                  <th class="border border-slate-300 px-2.5 py-2 text-center">Skor Akhir</th>
                  <th class="border border-slate-300 px-2.5 py-2 text-center">Predikat</th>
                </tr>
              </thead>
              <tbody>${summaryRowsHtml}</tbody>
            </table>
          </div>
          <p class="text-[11px] text-slate-500">Keterangan Skala: 1,00–1,50 (Kurang) | 1,51–2,50 (Cukup) | 2,51–3,50 (Baik / Memenuhi SNP) | 3,51–4,00 (Sangat Baik).</p>
        </div>

        <!-- Rincian Rekap Masing-Masing Kegiatan -->
        <div class="space-y-3">
          <h3 class="text-xs font-bold uppercase tracking-wider text-slate-800">II. Rekap Masing-Masing Kegiatan Pengawasan</h3>
          ${detailBlocksHtml}
        </div>

        <!-- Tanda Tangan -->
        <div class="pt-6 grid grid-cols-2 text-xs break-inside-avoid">
          <div></div>
          <div class="text-center space-y-16">
            <div>
              <p>${todayFormatted}</p>
              <p class="font-semibold">Pengawas Sekolah,</p>
            </div>
            <div>
              <p class="font-bold underline">${escapeHtml(p.name)}</p>
              <p>NIP. ${escapeHtml(p.nip || '-')}</p>
            </div>
          </div>
        </div>
      `;

      const modal = document.getElementById('previewModal');
      modal.classList.remove('hidden');
      modal.classList.add('flex');
    }

    function closePreviewModal() {
      const modal = document.getElementById('previewModal');
      modal.classList.add('hidden');
      modal.classList.remove('flex');
      document.body.classList.remove('printing-preview');
    }

    function printPreviewDocument() {
      document.body.classList.add('printing-preview');
      window.print();
      setTimeout(() => {
        document.body.classList.remove('printing-preview');
      }, 500);
    }

    function exportRekapCSV() {
      const tp = appState.tahunPelajaran || '2026/2027';
      const filterVal = document.getElementById('rekapSchoolFilter')?.value || 'all';
      const targetSchools = filterVal === 'all'
        ? appState.schools
        : appState.schools.filter(s => s.name === filterVal);

      if (targetSchools.length === 0) {
        showToast('Tidak ada data sekolah untuk diekspor.');
        return;
      }

      const headers = ['Tahun Pelajaran', 'Nama Sekolah', 'Jenjang', 'NPSN', 'Kepala Sekolah', 'Indikator Terisi', 'Rata-rata Pemantauan', 'Rata-rata Penilaian', 'Rata-rata Pembinaan', 'Jumlah Kegiatan Jurnal', 'Rata-rata Jurnal', 'Skor Akhir', 'Capaian (%)', 'Predikat Akhir'];
      const rows = targetSchools.map(s => {
        const r = calculateSchoolRecap(s);
        const avgP1 = r.pillarStats.pemantauan.count > 0 ? formatNum(r.pillarStats.pemantauan.sum / r.pillarStats.pemantauan.count) : '-';
        const avgP2 = r.pillarStats.penilaian.count > 0 ? formatNum(r.pillarStats.penilaian.sum / r.pillarStats.penilaian.count) : '-';
        const avgP3 = r.pillarStats.pembinaan.count > 0 ? formatNum(r.pillarStats.pembinaan.sum / r.pillarStats.pembinaan.count) : '-';
        return [
          tp,
          r.school.name,
          r.school.level,
          r.school.npsn || '-',
          r.school.principal,
          `${r.totalIndFilled}/16`,
          avgP1,
          avgP2,
          avgP3,
          r.schoolLogs.length,
          r.schoolLogs.length > 0 ? formatNum(r.avgLogScore) : '-',
          r.finalScore > 0 ? formatNum(r.finalScore) : '-',
          r.finalScore > 0 ? `${r.percentage.toFixed(1)}%` : '-',
          r.predikat.label
        ].map(v => `"${String(v).replace(/"/g, '""')}"`).join(',');
      });

      const csv = [headers.join(','), ...rows].join('\n');
      const blob = new Blob([csv], { type: 'text/csv;charset=utf-8;' });
      const url = URL.createObjectURL(blob);
      const a = document.createElement('a');
      a.href = url;
      a.download = `Rekap_Hasil_Akhir_SD_${tp.replace(/[\/\s]+/g, '_')}.csv`;
      a.click();
      URL.revokeObjectURL(url);
      showToast('CSV Rekap & Hasil Akhir SD berhasil diunduh.');
    }

    // ==================== TAB 5: KALKULATOR ANGKA KREDIT ====================
<!-- ... existing code ... -->
        appState.logs.unshift(newLog);
        renderLogs();
        renderRekapTab();
        document.getElementById('logFinding').value = '';
        document.getElementById('logRtl').value = '';
        document.getElementById('logEvidence').value = '';
        showToast('Kegiatan pengawasan berhasil dicatat.');
      });

      document.getElementById('searchLog').addEventListener('input', renderLogs);
      document.getElementById('filterLogPillar').addEventListener('change', renderLogs);
      document.getElementById('rekapSchoolFilter').addEventListener('change', renderRekapTab);
      document.getElementById('btnClosePreview').addEventListener('click', closePreviewModal);
      window.addEventListener('afterprint', () => {
        document.body.classList.remove('printing-preview');
      });

      // Form Sekolah Binaan
<!-- ... existing code ... -->
      // Render awal
      renderProfile();
      renderSchools();
      renderTahunPelajaran();
      selectAnalysisJenjang(appState.profile.jenjang || 'madya');
      renderLogs();
      renderRekapTab();
      renderAkCalculator();
    });
  </script>
</body>
</html># pengawashebat2
