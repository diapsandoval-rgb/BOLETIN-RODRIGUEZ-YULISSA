# BOLETIN-RODRIGUEZ-YULISSA
<html><html><head><meta charset="UTF-8"><script src="https://cdn.jsdelivr.net/npm/chart.js"></script><style>
        :root {
            --primario: #1a237e; --acento: #3d5afe; --fondo: #f8fafc;
            --blanco: #ffffff; --texto: #1e293b;
            --sob: #10b981; --nor: #f59e0b; --baj: #f97316; --cri: #ef4444;
        }

        body { font-family: 'Inter', 'Segoe UI', sans-serif; background: var(--fondo); color: var(--texto); margin: 0; }
        
        .auth-screen { position: fixed; inset: 0; background: linear-gradient(135deg, var(--primario), var(--acento)); display: flex; justify-content: center; align-items: center; z-index: 2000; }
        .auth-card { background: var(--blanco); padding: 40px; border-radius: 24px; width: 380px; text-align: center; box-shadow: 0 20px 25px -5px rgba(0,0,0,0.1); }
        .auth-card input { width: 100%; padding: 14px; margin: 10px 0; border: 1.5px solid #e2e8f0; border-radius: 12px; font-size: 1rem; }
        .btn-login { background: var(--acento); color: white; border: none; width: 100%; padding: 14px; border-radius: 12px; cursor: pointer; font-weight: 700; }

        .app { padding: 30px; max-width: 1500px; margin: auto; }
        .header { background: var(--blanco); padding: 20px; border-radius: 20px; display: flex; justify-content: space-between; align-items: center; margin-bottom: 25px; box-shadow: 0 4px 6px -1px rgba(0,0,0,0.05); }

        .creds-top-panel { background: #f0fdf4; border: 1px solid #bbf7d0; padding: 20px; border-radius: 20px; margin-bottom: 25px; display: none; }
        .creds-grid { display: grid; grid-template-columns: repeat(auto-fill, minmax(280px, 1fr)); gap: 10px; max-height: 200px; overflow-y: auto; padding: 10px; background: white; border-radius: 12px; }
        .cred-item { font-size: 0.8rem; border-bottom: 1px solid #f1f5f9; padding: 5px; }

        .admin-box { background: #eef2ff; padding: 20px; border-radius: 20px; margin-bottom: 25px; border: 2px dashed var(--acento); display: none; text-align: center; }
        
        .tabs { display: flex; gap: 15px; overflow-x: auto; padding-bottom: 15px; margin-bottom: 25px; }
        .tab-wrapper { background: var(--blanco); padding: 15px; border-radius: 18px; min-width: 180px; border: 2px solid transparent; box-shadow: 0 4px 6px rgba(0,0,0,0.05); transition: 0.3s; text-align: center; }
        .tab-wrapper.active { border-color: var(--acento); background: #f0f3ff; }
        
        .btn-view { background: var(--acento); color: white; width: 100%; margin-bottom: 5px; font-weight: bold; padding: 8px; border-radius: 8px; border: none; cursor: pointer; }
        .btn-icon { border: none; padding: 8px; border-radius: 8px; cursor: pointer; font-size: 1rem; }
        .btn-exp { background: #e0e7ff; color: var(--primario); }
        .btn-del { background: #fee2e2; color: var(--cri); }

        .stats-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(180px, 1fr)); gap: 15px; margin-bottom: 25px; }
        .stat-card { background: var(--blanco); padding: 20px; border-radius: 18px; text-align: center; box-shadow: 0 4px 6px rgba(0,0,0,0.05); }
        .stat-card h5 { margin: 0; color: #64748b; text-transform: uppercase; font-size: 0.75rem; }
        .stat-card .val { font-size: 1.8rem; font-weight: 800; color: var(--primario); margin: 5px 0; }
        .stat-card .desv { font-size: 0.7rem; color: var(--cri); font-weight: 700; background: #fff1f2; padding: 2px 8px; border-radius: 10px; display: inline-block; }

        .charts { display: grid; grid-template-columns: 1fr 2.5fr; gap: 25px; margin-bottom: 25px; }
        .chart-card { background: var(--blanco); padding: 25px; border-radius: 24px; box-shadow: 0 10px 15px rgba(0,0,0,0.05); min-height: 400px; }

        .card-table { background: var(--blanco); padding: 25px; border-radius: 24px; box-shadow: 0 10px 15px rgba(0,0,0,0.05); }
        table { width: 100%; border-collapse: collapse; }
        th { padding: 12px; font-size: 0.75rem; color: #94a3b8; text-transform: uppercase; border-bottom: 1px solid #f1f5f9; }
        td { padding: 12px; border-bottom: 1px solid #f8fafc; text-align: center; font-size: 0.9rem; }

        .badge { padding: 5px 12px; border-radius: 99px; font-weight: 700; font-size: 0.65rem; }
        .sob { background: #d1fae5; color: #065f46; }
        .nor { background: #fef3c7; color: #92400e; }
        .baj { background: #ffedd5; color: #9a3412; }
        .cri { background: #fee2e2; color: #991b1b; }
        
        .btn-indiv { background: #f1f5f9; color: var(--acento); border: none; padding: 5px; border-radius: 5px; cursor: pointer; }

        @media print { .no-print { display: none !important; } }
     .no-print { display:none !important; }</style></head><body><div class="app"><div class="header"><div><h2>Resultado Estudiante: RODRIGUEZ RODRIGUEZ YULISA</h2><p style="color:var(--acento); font-weight:bold;">I.E. La Esperanza</p></div><button class="no-print btn-view" style="width:auto; padding:10px 20px;" onclick="window.print()">Imprimir PDF</button></div><div id="statsGrid" class="stats-grid"></div><div class="charts"><div class="chart-card"><canvas id="pieChart"></canvas></div><div class="chart-card"><canvas id="barChart"></canvas></div></div><div class="card-table"><table><thead><tr><th>Pos</th><th style="text-align:left">Estudiante</th><th>LEC</th><th>MAT</th><th>SOC</th><th>NAT</th><th>ING</th><th style="color:#3d5afe">GLOBAL</th><th>NIVEL</th></tr></thead><tbody><tr><td>#27</td><td style="text-align:left; font-weight:600;">RODRIGUEZ RODRIGUEZ YULISA</td><td>35</td><td>64</td><td>52</td><td>40</td><td>44</td><td style="font-weight:800; color:#3d5afe">237</td><td><span class="badge baj">Bajo</span></td></tr></tbody></table></div></div><script>const e = {"nombre":"RODRIGUEZ RODRIGUEZ YULISA","lec":35,"mat":64,"soc":52,"cie":40,"ing":44,"global":237,"nivel":{"n":"Bajo","c":"baj"}}; const mtr = [{k:'lec', l:'Lectura'}, {k:'mat', l:'Mates'}, {k:'soc', l:'Sociales'}, {k:'cie', l:'Ciencias'}, {k:'ing', l:'Inglés'}, {k:'global', l:'Global'}]; document.getElementById('statsGrid').innerHTML = mtr.map(m => '<div class="stat-card"><h5>'+m.l+'</h5><div class="val">'+e[m.k]+'</div><div class="desv">Puntaje</div></div>').join(''); const lv={sob:0,nor:0,baj:0,cri:0}; lv[e.nivel.c]=1; new Chart(document.getElementById('pieChart'),{type:'doughnut',data:{labels:['Sobresaliente','Normal','Bajo','Crítico'],datasets:[{data:Object.values(lv),backgroundColor:['#10b981','#f59e0b','#f97316','#ef4444']}]},options:{maintainAspectRatio:false}}); new Chart(document.getElementById('barChart'),{type:'bar',data:{labels:['Lectura','Mates','Sociales','Ciencias','Inglés'],datasets:[{label:'Puntaje por Materias',data:[e.lec,e.mat,e.soc,e.cie,e.ing],backgroundColor:['#FF6384','#36A2EB','#FFCE56','#4BC0C0','#9966FF'],borderRadius:10}]},options:{maintainAspectRatio:false,plugins:{legend:{display:false}},scales:{y:{beginAtZero:true,max:100}}}});</script></body></html>
