<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Dashboard de Fabricación - ALW</title>
    <style>
        :root {
            --primary: #1a1f36;
            --secondary: #2d3748;
            --accent: #3182ce;
            --success: #38a169;
            --warning: #d69e2e;
            --danger: #e53e3e;
            --text: #e2e8f0;
            --text-muted: #a0aec0;
            --border: #4a5568;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        body {
            background: linear-gradient(135deg, #0f172a, #1e293b);
            color: var(--text);
            line-height: 1.6;
            min-height: 100vh;
        }

        .dashboard-container {
            display: grid;
            grid-template-columns: 1fr 350px;
            gap: 20px;
            max-width: 1800px;
            margin: 0 auto;
            padding: 20px;
        }

        /* HEADER STYLES */
        .dashboard-header {
            grid-column: 1 / -1;
            background: var(--primary);
            color: var(--text);
            padding: 1.5rem 2rem;
            border-radius: 12px;
            margin-bottom: 2rem;
            box-shadow: 0 4px 12px rgba(0,0,0,0.3);
            display: flex;
            justify-content: space-between;
            align-items: center;
            border: 1px solid var(--border);
        }

        .header-brand {
            display: flex;
            align-items: center;
            gap: 1.5rem;
        }

        .logo {
            height: 50px;
            width: auto;
        }

        .brand-text h1 {
            font-size: 1.8rem;
            margin-bottom: 0.5rem;
            background: linear-gradient(135deg, #63b3ed, #4299e1);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }

        .brand-text p {
            opacity: 0.8;
            font-size: 1rem;
        }

        .header-stats {
            display: flex;
            gap: 2rem;
        }

        .stat-item {
            text-align: center;
        }

        .stat-value {
            font-size: 1.8rem;
            font-weight: 700;
            margin-bottom: 0.2rem;
        }

        .stat-label {
            font-size: 0.85rem;
            opacity: 0.8;
            text-transform: uppercase;
            letter-spacing: 1px;
        }

        /* MAIN CONTENT GRID */
        .main-content {
            display: flex;
            flex-direction: column;
            gap: 20px;
        }

        /* AREA SECTIONS */
        .area-section {
            background: var(--primary);
            border-radius: 12px;
            padding: 1.5rem;
            box-shadow: 0 4px 6px rgba(0,0,0,0.2);
            border: 1px solid var(--border);
        }

        .area-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 1.5rem;
            padding-bottom: 0.75rem;
            border-bottom: 1px solid var(--border);
        }

        .area-title {
            font-size: 1.4rem;
            font-weight: 600;
            color: var(--text);
        }

        .area-machines {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
            gap: 1.5rem;
        }

        /* MACHINE CARD STYLES */
        .machine {
            background: var(--secondary);
            border-radius: 10px;
            padding: 1.5rem;
            box-shadow: 0 4px 8px rgba(0,0,0,0.2);
            border-left: 4px solid var(--accent);
            transition: transform 0.3s, box-shadow 0.3s;
            border: 1px solid var(--border);
        }

        .machine:hover {
            transform: translateY(-5px);
            box-shadow: 0 8px 15px rgba(0,0,0,0.3);
        }

        .machine.stopped {
            border-left-color: var(--danger);
        }

        .machine-header {
            display: flex;
            justify-content: space-between;
            align-items: flex-start;
            margin-bottom: 1rem;
        }

        .machine-name {
            font-size: 1.2rem;
            font-weight: 600;
            color: var(--text);
        }

        .machine-status {
            padding: 0.3rem 0.8rem;
            border-radius: 20px;
            font-size: 0.75rem;
            font-weight: 600;
            text-transform: uppercase;
        }

        .status-running {
            background-color: rgba(56, 161, 105, 0.2);
            color: var(--success);
            border: 1px solid var(--success);
        }

        .status-stopped {
            background-color: rgba(229, 62, 62, 0.2);
            color: var(--danger);
            border: 1px solid var(--danger);
        }

        .machine-timer {
            background: rgba(229, 62, 62, 0.1);
            padding: 0.5rem;
            border-radius: 6px;
            text-align: center;
            font-weight: 600;
            color: var(--danger);
            margin-bottom: 1rem;
            font-size: 0.9rem;
            border: 1px solid var(--danger);
        }

        .machine-metrics {
            display: flex;
            justify-content: space-between;
            margin-bottom: 1.5rem;
        }

        .metric {
            text-align: center;
        }

        .metric-value {
            font-size: 1.5rem;
            font-weight: 700;
            color: var(--text);
        }

        .metric-label {
            font-size: 0.8rem;
            color: var(--text-muted);
            text-transform: uppercase;
            letter-spacing: 0.5px;
        }

        .machine-actions {
            display: flex;
            gap: 0.5rem;
        }

        .btn-machine {
            flex: 1;
            padding: 0.6rem 0.5rem;
            border: none;
            border-radius: 6px;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s;
            font-size: 0.85rem;
            text-align: center;
        }

        .btn-stop {
            background-color: var(--danger);
            color: white;
        }

        .btn-stop:hover {
            background-color: #c53030;
        }

        .btn-run {
            background-color: var(--success);
            color: white;
        }

        .btn-run:hover {
            background-color: #2f855a;
        }

        /* PRODUCTION REGISTRATION */
        .production-section {
            background: var(--primary);
            border-radius: 12px;
            padding: 1.5rem;
            box-shadow: 0 4px 6px rgba(0,0,0,0.2);
            border: 1px solid var(--border);
        }

        .production-form {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 1rem;
            margin-top: 1rem;
        }

        .form-group {
            display: flex;
            flex-direction: column;
        }

        .form-group.full-width {
            grid-column: 1 / -1;
        }

        label {
            margin-bottom: 0.5rem;
            font-weight: 600;
            color: var(--text);
        }

        select, input, textarea {
            padding: 0.75rem;
            background: var(--secondary);
            border: 1px solid var(--border);
            border-radius: 6px;
            color: var(--text);
            font-size: 1rem;
        }

        select:focus, input:focus, textarea:focus {
            outline: none;
            border-color: var(--accent);
            box-shadow: 0 0 0 2px rgba(49, 130, 206, 0.2);
        }

        .btn-primary {
            background: var(--accent);
            color: white;
            border: none;
            padding: 0.75rem 1.5rem;
            border-radius: 6px;
            font-weight: 600;
            cursor: pointer;
            transition: background 0.3s;
        }

        .btn-primary:hover {
            background: #2b6cb0;
        }

        /* TOP 5 SECTION */
        .top5-section {
            background: var(--primary);
            border-radius: 12px;
            padding: 1.5rem;
            box-shadow: 0 4px 6px rgba(0,0,0,0.2);
            border: 1px solid var(--border);
        }

        .top5-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 1.5rem;
            padding-bottom: 0.75rem;
            border-bottom: 1px solid var(--border);
        }

        .top5-title {
            font-size: 1.4rem;
            font-weight: 600;
            color: var(--text);
        }

        .pareto-container {
            display: flex;
            flex-direction: column;
            gap: 1rem;
        }

        .pareto-item {
            display: flex;
            align-items: center;
            padding: 1rem;
            background: var(--secondary);
            border-radius: 8px;
            transition: transform 0.2s;
            border: 1px solid var(--border);
        }

        .pareto-item:hover {
            transform: translateX(5px);
            background: #374151;
        }

        .pareto-rank {
            font-size: 1.2rem;
            font-weight: 700;
            color: var(--text);
            width: 40px;
            text-align: center;
        }

        .pareto-info {
            flex: 1;
            margin: 0 1rem;
        }

        .pareto-machine {
            font-weight: 600;
            color: var(--text);
        }

        .pareto-area {
            font-size: 0.85rem;
            color: var(--text-muted);
        }

        .pareto-bar-container {
            flex: 2;
            margin: 0 1rem;
        }

        .pareto-bar {
            height: 20px;
            background: #4a5568;
            border-radius: 10px;
            overflow: hidden;
        }

        .pareto-fill {
            height: 100%;
            background: linear-gradient(90deg, var(--danger), #fc8181);
            border-radius: 10px;
            transition: width 1s ease;
        }

        .pareto-time {
            font-weight: 600;
            color: var(--danger);
            width: 70px;
            text-align: right;
        }

        /* SIDEBAR - HISTORIAL */
        .sidebar {
            display: flex;
            flex-direction: column;
            gap: 20px;
        }

        .history-section {
            background: var(--primary);
            border-radius: 12px;
            padding: 1.5rem;
            box-shadow: 0 4px 6px rgba(0,0,0,0.2);
            border: 1px solid var(--border);
            flex: 1;
        }

        .history-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 1.5rem;
            padding-bottom: 0.75rem;
            border-bottom: 1px solid var(--border);
        }

        .history-title {
            font-size: 1.4rem;
            font-weight: 600;
            color: var(--text);
        }

        .history-list {
            max-height: 600px;
            overflow-y: auto;
        }

        .history-item {
            padding: 1rem;
            background: var(--secondary);
            border-radius: 8px;
            margin-bottom: 0.75rem;
            border-left: 4px solid var(--accent);
            border: 1px solid var(--border);
        }

        .history-item.stop {
            border-left-color: var(--danger);
        }

        .history-item.run {
            border-left-color: var(--success);
        }

        .history-item.production {
            border-left-color: var(--accent);
        }

        .history-time {
            font-size: 0.8rem;
            color: var(--text-muted);
            margin-bottom: 0.5rem;
        }

        .history-content {
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .history-machine {
            font-weight: 600;
            color: var(--text);
        }

        .history-action {
            padding: 0.3rem 0.8rem;
            border-radius: 20px;
            font-size: 0.75rem;
            font-weight: 600;
            text-transform: uppercase;
        }

        .action-stop {
            background: rgba(229, 62, 62, 0.2);
            color: var(--danger);
        }

        .action-run {
            background: rgba(56, 161, 105, 0.2);
            color: var(--success);
        }

        .action-production {
            background: rgba(49, 130, 206, 0.2);
            color: var(--accent);
        }

        /* MODAL STYLES */
        .modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0,0,0,0.7);
            z-index: 1000;
            align-items: center;
            justify-content: center;
        }

        .modal-content {
            background: var(--primary);
            border-radius: 12px;
            width: 90%;
            max-width: 500px;
            box-shadow: 0 10px 30px rgba(0,0,0,0.4);
            overflow: hidden;
            animation: modalAppear 0.3s ease;
            border: 1px solid var(--border);
        }

        @keyframes modalAppear {
            from { opacity: 0; transform: translateY(-20px); }
            to { opacity: 1; transform: translateY(0); }
        }

        .modal-header {
            padding: 1.5rem;
            background: var(--secondary);
            color: var(--text);
            border-bottom: 1px solid var(--border);
        }

        .modal-title {
            font-size: 1.4rem;
            font-weight: 600;
            margin-bottom: 0.5rem;
        }

        .machine-info {
            font-size: 0.95rem;
            opacity: 0.9;
        }

        form {
            padding: 1.5rem;
        }

        .btn-group {
            display: flex;
            gap: 1rem;
            margin-top: 1.5rem;
        }

        .btn-cancel, .btn-confirm {
            flex: 1;
            padding: 0.75rem;
            border: none;
            border-radius: 6px;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s;
        }

        .btn-cancel {
            background: var(--secondary);
            color: var(--text);
            border: 1px solid var(--border);
        }

        .btn-cancel:hover {
            background: #374151;
        }

        .btn-confirm {
            background: var(--accent);
            color: white;
        }

        .btn-confirm:hover {
            background: #2b6cb0;
        }

        /* RESPONSIVE DESIGN */
        @media (max-width: 1200px) {
            .dashboard-container {
                grid-template-columns: 1fr;
            }
            
            .sidebar {
                grid-column: 1 / -1;
                flex-direction: row;
            }
            
            .history-section {
                flex: 1;
            }
        }

        @media (max-width: 768px) {
            .dashboard-header {
                flex-direction: column;
                text-align: center;
                gap: 1.5rem;
            }
            
            .header-stats {
                width: 100%;
                justify-content: space-around;
            }
            
            .area-machines {
                grid-template-columns: 1fr;
            }
            
            .production-form {
                grid-template-columns: 1fr;
            }
            
            .machine-actions {
                flex-direction: column;
            }
            
            .sidebar {
                flex-direction: column;
            }
        }

        /* SCROLLBAR STYLING */
        ::-webkit-scrollbar {
            width: 8px;
        }

        ::-webkit-scrollbar-track {
            background: var(--secondary);
            border-radius: 4px;
        }

        ::-webkit-scrollbar-thumb {
            background: var(--accent);
            border-radius: 4px;
        }

        ::-webkit-scrollbar-thumb:hover {
            background: #2b6cb0;
        }
    </style>
</head>
<body>
    <div class="dashboard-container">
        <!-- HEADER -->
        <header class="dashboard-header">
            <div class="header-brand">
                <div class="logo-placeholder" style="height: 50px; width: 150px; background: linear-gradient(135deg, #3182ce, #63b3ed); color: white; display: flex; align-items: center; justify-content: center; font-weight: bold; border-radius: 8px; font-size: 1.5rem; border: 2px solid #63b3ed;">
    ALW
</div>
                <div class="brand-text">
                    <h1>Dashboard de Fabricación</h1>
                    <p>Monitoreo en tiempo real de producción y eficiencia</p>
                    <div id="liveDate" style="margin-top: 10px; font-size: 0.9rem;"></div>
                    <div id="weekSystem" style="font-size: 0.8rem; opacity: 0.8;"></div>
                </div>
            </div>
            <div class="header-stats">
                <div class="stat-item">
                    <div class="stat-value" id="overallAvailability">95.2%</div>
                    <div class="stat-label">Disponibilidad</div>
                </div>
                <div class="stat-item">
                    <div class="stat-value" id="activeMachines">42/48</div>
                    <div class="stat-label">Máquinas Activas</div>
                </div>
                <div class="stat-item">
                    <div class="stat-value" id="monthlyDowntime">18.5h</div>
                    <div class="stat-label">Tiempo Muerto</div>
                </div>
                <div class="stat-item">
                    <div class="stat-value" id="liveTime">14:23:45</div>
                    <div class="stat-label">Hora Actual</div>
                </div>
            </div>
        </header>

        <!-- MAIN CONTENT -->
        <div class="main-content">
            <!-- PRODUCTION REGISTRATION -->
            <div class="production-section">
                <div class="area-header">
                    <div class="area-title">Registro de Producción</div>
                </div>
                <form id="productionForm" class="production-form">
                    <div class="form-group">
                        <label for="productionMachine">Máquina:</label>
                        <select id="productionMachine" required>
                            <option value="">Seleccionar máquina...</option>
                        </select>
                    </div>
                    <div class="form-group">
                        <label for="productionProduct">Producto:</label>
                        <input type="text" id="productionProduct" placeholder="Nombre del producto" required>
                    </div>
                    <div class="form-group">
                        <label for="productionQuantity">Cantidad:</label>
                        <input type="number" id="productionQuantity" placeholder="Cantidad producida" required min="1">
                    </div>
                    <div class="form-group">
                        <label for="productionOperator">Operador:</label>
                        <input type="text" id="productionOperator" placeholder="Nombre del operador" required>
                    </div>
                    <div class="form-group full-width">
                        <label for="productionNotes">Notas:</label>
                        <textarea id="productionNotes" rows="2" placeholder="Observaciones adicionales..."></textarea>
                    </div>
                    <div class="form-group full-width">
                        <button type="submit" class="btn-primary">Registrar Producción</button>
                    </div>
                </form>
            </div>

            <!-- ÁREAS DE PRODUCCIÓN -->
            <div class="area-section">
                <div class="area-header">
                    <div class="area-title">Corte y Maquinado</div>
                </div>
                <div class="area-machines" id="area-corte">
                    <!-- Máquinas se generan dinámicamente -->
                </div>
            </div>

            <div class="area-section">
                <div class="area-header">
                    <div class="area-title">CNC</div>
                </div>
                <div class="area-machines" id="area-cnc">
                    <!-- Máquinas se generan dinámicamente -->
                </div>
            </div>

            <div class="area-section">
                <div class="area-header">
                    <div class="area-title">Sheet Metal</div>
                </div>
                <div class="area-machines" id="area-sheetmetal">
                    <!-- Máquinas se generan dinámicamente -->
                </div>
            </div>

            <div class="area-section">
                <div class="area-header">
                    <div class="area-title">Rolado</div>
                </div>
                <div class="area-machines" id="area-rolado">
                    <!-- Máquinas se generan dinámicamente -->
                </div>
            </div>

            <div class="area-section">
                <div class="area-header">
                    <div class="area-title">Soldadura</div>
                </div>
                <div class="area-machines" id="area-soldadura">
                    <!-- Máquinas se generan dinámicamente -->
                </div>
            </div>

            <div class="area-section">
                <div class="area-header">
                    <div class="area-title">Detallado</div>
                </div>
                <div class="area-machines" id="area-detallado">
                    <!-- Máquinas se generan dinámicamente -->
                </div>
            </div>

            <!-- TOP 5 -->
            <div class="top5-section">
                <div class="top5-header">
                    <div class="top5-title">Top 5 - Máquinas con Mayor Tiempo Muerto</div>
                </div>
                <div class="pareto-container" id="paretoChart">
                    <!-- Pareto se genera dinámicamente -->
                </div>
            </div>
        </div>

        <!-- SIDEBAR - HISTORIAL -->
        <div class="sidebar">
            <div class="history-section">
                <div class="history-header">
                    <div class="history-title">Historial de Eventos</div>
                </div>
                <div class="history-list" id="historyList">
                    <!-- Historial se genera dinámicamente -->
                </div>
            </div>
        </div>
    </div>

    <!-- MODALES -->
    <div id="stopModal" class="modal">
        <div class="modal-content">
            <div class="modal-header">
                <div class="modal-title">Detener Máquina</div>
                <div class="machine-info">
                    <div id="stopMachineName" style="font-size: 1.2em; font-weight: 600;"></div>
                    <div id="stopAreaName" style="opacity: 0.8; font-size: 0.9em;"></div>
                </div>
            </div>
            
            <form id="stopForm">
                <div class="form-group">
                    <label>Motivo de la Parada:</label>
                    <select id="stopReason" required>
                        <option value="">Seleccionar motivo...</option>
                        <option value="Mantenimiento Preventivo">Mantenimiento Preventivo</option>
                        <option value="Falla Mecánica">Falla Mecánica</option>
                        <option value="Falla Eléctrica">Falla Eléctrica</option>
                        <option value="Falta de Material">Falta de Material</option>
                        <option value="Cambio de Herramienta">Cambio de Herramienta</option>
                        <option value="Setup/Programación">Setup/Programación</option>
                        <option value="Sin Operador">Sin Operador</option>
                        <option value="Calidad/Inspección">Calidad/Inspección</option>
                        <option value="Limpieza">Limpieza</option>
                        <option value="Otro">Otro</option>
                    </select>
                </div>
                
                <div class="form-group">
                    <label>Descripción Detallada:</label>
                    <textarea id="stopDescription" rows="3" placeholder="Describa el problema o actividad..." required></textarea>
                </div>
                
                <div class="form-group">
                    <label>Operador Responsable:</label>
                    <input type="text" id="operatorName" placeholder="Nombre del operador" required>
                </div>
                
                <div class="btn-group">
                    <button type="button" class="btn-cancel" onclick="closeStopModal()">Cancelar</button>
                    <button type="submit" class="btn-confirm">Confirmar Parada</button>
                </div>
            </form>
        </div>
    </div>

    <div id="runModal" class="modal">
        <div class="modal-content">
            <div class="modal-header">
                <div class="modal-title">Reanudar Operación</div>
                <div class="machine-info">
                    <div id="runMachineName" style="font-size: 1.2em; font-weight: 600;"></div>
                    <div id="runAreaName" style="opacity: 0.8; font-size: 0.9em;"></div>
                    <div id="runDowntime" style="color: var(--danger); font-weight: 600; margin-top: 5px; font-size: 0.9em;"></div>
                </div>
            </div>
            
            <form id="runForm">
                <div class="form-group">
                    <label>Acciones Realizadas:</label>
                    <select id="repairAction" required>
                        <option value="">Seleccionar acción...</option>
                        <option value="Reparación Mecánica">Reparación Mecánica</option>
                        <option value="Reparación Eléctrica">Reparación Eléctrica</option>
                        <option value="Ajuste/Calibración">Ajuste/Calibración</option>
                        <option value="Cambio de Componente">Cambio de Componente</option>
                        <option value="Lubricación">Lubricación</option>
                        <option value="Limpieza General">Limpieza General</option>
                        <option value="Programación/Setup">Programación/Setup</option>
                        <option value="Inspección de Calidad">Inspección de Calidad</option>
                        <option value="Otro">Otro</option>
                    </select>
                </div>
                
                <div class="form-group">
                    <label>Descripción de la Reparación:</label>
                    <textarea id="repairDescription" rows="3" placeholder="Describa las acciones realizadas..." required></textarea>
                </div>
                
                <div class="form-group">
                    <label>Técnico Responsable:</label>
                    <input type="text" id="technicianName" placeholder="Nombre del técnico" required>
                </div>
                
                <div class="btn-group">
                    <button type="button" class="btn-cancel" onclick="closeRunModal()">Cancelar</button>
                    <button type="submit" class="btn-confirm">Reanudar Máquina</button>
                </div>
            </form>
        </div>
    </div>

    <script>
        // CONFIGURACIÓN SHAREPOINT
        const SHAREPOINT_CONFIG = {
            siteUrl: "https://lumenpulse.sharepoint.com/sites/ALWSistemaProduccin",
            lists: {
                machines: "Maquinas_Catalogo",
                downtime: "Downtime_Registros",
                production: "Produccion_Registros"
            }
        };

        // DATOS DE MÁQUINAS
        const machineData = {
            'corte': ['ChopSaw 1', 'ChopSaw 2', 'CDT', 'PMI 1', 'PMI 2', 'CTD', 'Fresadora 1', 'Fresadora 2', 'Fresadora 3', 'Fresadora 4', 'Fresadora 5'],
            'cnc': ['Cierra Banda', 'Fadal 1', 'Fadal 2', 'Fadal 3', 'Fadal 4', 'Fadal 5', 'MORI', 'Fresadora 1'],
            'sheetmetal': ['Laser 3015', 'AE', 'Vipros 255', 'Dobladora 1', 'Dobladora 2', 'Dobladora 3'],
            'rolado': ['Roladora 1', 'Roladora 2', 'Roladora 3', 'CTD'],
            'soldadura': ['Miller 1', 'Miller 2', 'Miller 3', 'Miller 4', 'Miller 5'],
            'detallado': ['Tumbler', 'Corn', 'Lijabanda 1', 'Lijabanda 2', 'Lijabanda 3', 'Lijabanda 4']
        };

        const areaNames = {
            'corte': 'Corte y Maquinado',
            'cnc': 'CNC',
            'sheetmetal': 'Sheet Metal',
            'rolado': 'Rolado',
            'soldadura': 'Soldadura',
            'detallado': 'Detallado'
        };

        let machines = {};
        let records = [];
        let currentStoppedMachine = null;
        let history = [];

        // INICIALIZAR SISTEMA
        function initializeSystem() {
            initializeMachines();
            populateMachineDropdown();
            renderAllAreas();
            renderParetoChart();
            updateHeaderStats();
            startLiveClock();
            startMachineTimers();
            loadHistory();
            
            // Cargar datos iniciales
            loadInitialData();
        }

        // POBLAR DROPDOWN DE MÁQUINAS PARA PRODUCCIÓN
        function populateMachineDropdown() {
            const dropdown = document.getElementById('productionMachine');
            dropdown.innerHTML = '<option value="">Seleccionar máquina...</option>';
            
            for (const [area, machineList] of Object.entries(machineData)) {
                machineList.forEach(machineName => {
                    const option = document.createElement('option');
                    option.value = `${area}-${machineName.replace(/\s+/g, '-').toLowerCase()}`;
                    option.textContent = `${machineName} (${areaNames[area]})`;
                    dropdown.appendChild(option);
                });
            }
        }

        // CARGAR HISTORIAL
        function loadHistory() {
            // Historial de ejemplo
            history = [
                { type: 'production', machine: 'Laser 3015', area: 'sheetmetal', details: 'Producción: 150 unidades - Componente A', time: new Date(Date.now() - 300000) },
                { type: 'stop', machine: 'Fresadora 1', area: 'corte', details: 'Parada: Mantenimiento preventivo', time: new Date(Date.now() - 900000) },
                { type: 'run', machine: 'Miller 3', area: 'soldadura', details: 'Reanudación: Reparación completada', time: new Date(Date.now() - 1800000) },
                { type: 'production', machine: 'Fadal 2', area: 'cnc', details: 'Producción: 80 unidades - Componente B', time: new Date(Date.now() - 3600000) }
            ];
            
            renderHistory();
        }

        // RENDERIZAR HISTORIAL
        function renderHistory() {
            const container = document.getElementById('historyList');
            container.innerHTML = '';
            
            history.sort((a, b) => b.time - a.time).forEach(item => {
                const historyItem = document.createElement('div');
                historyItem.className = `history-item ${item.type}`;
                
                const timeString = item.time.toLocaleTimeString('es-ES', { 
                    hour: '2-digit', 
                    minute: '2-digit'
                });
                
                const actionClass = `action-${item.type}`;
                const actionText = item.type === 'stop' ? 'DETENIDA' : 
                                 item.type === 'run' ? 'REANUDADA' : 'PRODUCCIÓN';
                
                historyItem.innerHTML = `
                    <div class="history-time">${timeString}</div>
                    <div class="history-content">
                        <div>
                            <div class="history-machine">${item.machine}</div>
                            <div style="font-size: 0.8rem; opacity: 0.8;">${item.details}</div>
                        </div>
                        <div class="history-action ${actionClass}">${actionText}</div>
                    </div>
                `;
                
                container.appendChild(historyItem);
            });
        }

        // AÑADIR AL HISTORIAL
        function addToHistory(type, machineId, details) {
            const machine = machines[machineId];
            if (!machine) return;
            
            history.unshift({
                type: type,
                machine: machine.name,
                area: machine.area,
                details: details,
                time: new Date()
            });
            
            // Mantener solo los últimos 50 eventos
            if (history.length > 50) {
                history.pop();
            }
            
            renderHistory();
        }

        // MANEJAR FORMULARIO DE PRODUCCIÓN
        document.getElementById('productionForm').addEventListener('submit', async function(e) {
            e.preventDefault();
            
            const machineId = document.getElementById('productionMachine').value;
            const product = document.getElementById('productionProduct').value;
            const quantity = document.getElementById('productionQuantity').value;
            const operator = document.getElementById('productionOperator').value;
            const notes = document.getElementById('productionNotes').value;
            
            const machine = machines[machineId];
            if (!machine) return;
            
            // Crear registro para SharePoint
            const record = {
                Title: `Producción - ${machine.name}`,
                MaquinaID: machineId,
                MaquinaNombre: machine.name,
                Area: machine.area,
                Producto: product,
                Cantidad: quantity,
                Operador: operator,
                Notas: notes,
                FechaHora: new Date().toISOString()
            };
            
            try {
                // Guardar en SharePoint
                await saveToSharePoint(SHAREPOINT_CONFIG.lists.production, record);
                
                // Añadir al historial
                addToHistory('production', machineId, `Producción: ${quantity} unidades - ${product}`);
                
                // Limpiar formulario
                document.getElementById('productionForm').reset();
                
                showNotification(`Producción registrada para ${machine.name}`, 'success');
            } catch (error) {
                showNotification('Error al guardar en SharePoint', 'error');
            }
        });

        // ... (el resto del código JavaScript permanece igual que en la versión anterior)

        // INICIALIZAR MÁQUINAS
        function initializeMachines() {
            for (const [area, machineList] of Object.entries(machineData)) {
                machineList.forEach(machineName => {
                    const machineId = `${area}-${machineName.replace(/\s+/g, '-').toLowerCase()}`;
                    
                    if (!machines[machineId]) {
                        machines[machineId] = {
                            id: machineId,
                            name: machineName,
                            area: area,
                            status: 'running',
                            availability: 98 + Math.random() * 2,
                            lastStopTime: null,
                            totalDowntime: 0
                        };
                    }
                });
            }
        }

        // RENDERIZAR TODAS LAS ÁREAS
        function renderAllAreas() {
            for (const area of Object.keys(machineData)) {
                renderArea(area);
            }
        }

        // RENDERIZAR ÁREA ESPECÍFICA
        function renderArea(area) {
            const container = document.getElementById(`area-${area}`);
            if (!container) return;

            container.innerHTML = '';
            const areaMachines = machineData[area];
            
            areaMachines.forEach(machineName => {
                const machineId = `${area}-${machineName.replace(/\s+/g, '-').toLowerCase()}`;
                const machine = machines[machineId];
                
                if (machine) {
                    const machineElement = createMachineElement(machine);
                    container.appendChild(machineElement);
                }
            });
        }

        // CREAR ELEMENTO DE MÁQUINA
        function createMachineElement(machine) {
            const div = document.createElement('div');
            div.className = `machine ${machine.status}`;
            
            const timerHtml = machine.status === 'stopped' ? 
                `<div class="machine-timer" id="timer-${machine.id}">⏱️ 00:00:00</div>` : '';
            
            div.innerHTML = `
                <div class="machine-header">
                    <div class="machine-name">${machine.name}</div>
                    <div class="machine-status ${machine.status === 'running' ? 'status-running' : 'status-stopped'}">
                        ${machine.status === 'running' ? 'EN OPERACIÓN' : 'DETENIDA'}
                    </div>
                </div>
                ${timerHtml}
                <div class="machine-metrics">
                    <div class="metric">
                        <div class="metric-value">${machine.availability.toFixed(1)}%</div>
                        <div class="metric-label">Availability</div>
                    </div>
                </div>
                <div class="machine-actions">
                    <button class="btn-machine btn-stop" onclick="openStopModal('${machine.id}')">
                        DETENER
                    </button>
                    <button class="btn-machine btn-run" onclick="openRunModal('${machine.id}')">
                        REANUDAR
                    </button>
                </div>
            `;
            return div;
        }

        // ACTUALIZAR TIMERS DE MÁQUINAS DETENIDAS
        function startMachineTimers() {
            setInterval(() => {
                for (const machineId in machines) {
                    const machine = machines[machineId];
                    if (machine.status === 'stopped' && machine.lastStopTime) {
                        const downtime = Math.floor((Date.now() - machine.lastStopTime) / 1000);
                        const timerElement = document.getElementById(`timer-${machineId}`);
                        if (timerElement) {
                            const hours = Math.floor(downtime / 3600).toString().padStart(2, '0');
                            const minutes = Math.floor((downtime % 3600) / 60).toString().padStart(2, '0');
                            const seconds = (downtime % 60).toString().padStart(2, '0');
                            timerElement.textContent = `⏱️ ${hours}:${minutes}:${seconds}`;
                        }
                    }
                }
            }, 1000);
        }

        // MOSTRAR NOTIFICACIÓN
        function showNotification(message, type = 'info') {
            const notification = document.createElement('div');
            notification.style.cssText = `
                position: fixed;
                top: 20px;
                right: 20px;
                padding: 15px 20px;
                border-radius: 8px;
                color: white;
                font-weight: 600;
                z-index: 10000;
                animation: slideIn 0.3s ease;
                max-width: 300px;
                background: ${type === 'success' ? '#38a169' : type === 'error' ? '#e53e3e' : '#3182ce'};
                box-shadow: 0 8px 25px rgba(0,0,0,0.4);
            `;
            notification.textContent = message;
            
            document.body.appendChild(notification);
            
            setTimeout(() => {
                notification.remove();
            }, 4000);
        }

        // MODALES
        function openStopModal(machineId) {
            const machine = machines[machineId];
            if (!machine || machine.status === 'stopped') return;
            
            currentStoppedMachine = machineId;
            document.getElementById('stopMachineName').textContent = machine.name;
            document.getElementById('stopAreaName').textContent = areaNames[machine.area];
            document.getElementById('stopModal').style.display = 'block';
        }

        function closeStopModal() {
            document.getElementById('stopModal').style.display = 'none';
            currentStoppedMachine = null;
            document.getElementById('stopForm').reset();
        }

        function openRunModal(machineId) {
            const machine = machines[machineId];
            if (!machine || machine.status === 'running') return;
            
            currentStoppedMachine = machineId;
            const downtime = calculateDowntime(machine.lastStopTime);
            
            document.getElementById('runMachineName').textContent = machine.name;
            document.getElementById('runAreaName').textContent = areaNames[machine.area];
            document.getElementById('runDowntime').textContent = `Tiempo de parada: ${formatTime(downtime)}`;
            document.getElementById('runModal').style.display = 'block';
        }

        function closeRunModal() {
            document.getElementById('runModal').style.display = 'none';
            currentStoppedMachine = null;
            document.getElementById('runForm').reset();
        }

        // CALCULAR TIEMPO DE PARADA
        function calculateDowntime(startTime) {
            return startTime ? (Date.now() - startTime) / 1000 : 0;
        }

        // FORMATEAR TIEMPO
        function formatTime(seconds) {
            const hours = Math.floor(seconds / 3600);
            const minutes = Math.floor((seconds % 3600) / 60);
            const secs = Math.floor(seconds % 60);
            return `${hours.toString().padStart(2, '0')}:${minutes.toString().padStart(2, '0')}:${secs.toString().padStart(2, '0')}`;
        }

        // MANEJAR FORMULARIO DE PARADA
        document.getElementById('stopForm').addEventListener('submit', async function(e) {
            e.preventDefault();
            
            const machineId = currentStoppedMachine;
            const machine = machines[machineId];
            
            if (machine) {
                // Actualizar estado de la máquina
                machine.status = 'stopped';
                machine.lastStopTime = Date.now();
                
                // Crear registro para SharePoint
                const record = {
                    Title: `Parada - ${machine.name}`,
                    MaquinaID: machineId,
                    MaquinaNombre: machine.name,
                    Area: machine.area,
                    Accion: 'stop',
                    Motivo: document.getElementById('stopReason').value,
                    Descripcion: document.getElementById('stopDescription').value,
                    Operador: document.getElementById('operatorName').value,
                    TiempoParada: 0,
                    FechaHora: new Date().toISOString()
                };
                
                try {
                    // Guardar en SharePoint
                    await saveToSharePoint(SHAREPOINT_CONFIG.lists.downtime, record);
                    
                    // Añadir al historial
                    addToHistory('stop', machineId, `Parada: ${document.getElementById('stopReason').value}`);
                    
                    // Actualizar interfaz
                    renderArea(machine.area);
                    updateHeaderStats();
                    
                    closeStopModal();
                    showNotification(`Máquina ${machine.name} detenida correctamente`, 'success');
                } catch (error) {
                    showNotification('Error al guardar en SharePoint', 'error');
                }
            }
        });

        // MANEJAR FORMULARIO DE REANUDACIÓN
        document.getElementById('runForm').addEventListener('submit', async function(e) {
            e.preventDefault();
            
            const machineId = currentStoppedMachine;
            const machine = machines[machineId];
            const technician = document.getElementById('technicianName').value;
            
            if (machine && machine.lastStopTime) {
                const downtime = (Date.now() - machine.lastStopTime) / 1000;
                
                // Actualizar estado de la máquina
                machine.status = 'running';
                machine.totalDowntime += downtime;
                machine.availability = Math.max(85, machine.availability - (downtime / 3600));
                
                // Crear registro para SharePoint
                const record = {
                    Title: `Reanudación - ${machine.name}`,
                    MaquinaID: machineId,
                    MaquinaNombre: machine.name,
                    Area: machine.area,
                    Accion: 'run',
                    Motivo: document.getElementById('repairAction').value,
                    Descripcion: document.getElementById('repairDescription').value,
                    Tecnico: technician,
                    TiempoParada: downtime,
                    FechaHora: new Date().toISOString()
                };
                
                try {
                    // Guardar en SharePoint
                    await saveToSharePoint(SHAREPOINT_CONFIG.lists.downtime, record);
                    
                    // Añadir al historial
                    addToHistory('run', machineId, `Reanudación: ${document.getElementById('repairAction').value}`);
                    
                    // Actualizar interfaz
                    renderArea(machine.area);
                    updateHeaderStats();
                    renderParetoChart();
                    
                    closeRunModal();
                    showNotification(`Máquina ${machine.name} reanudada correctamente`, 'success');
                } catch (error) {
                    showNotification('Error al guardar en SharePoint', 'error');
                }
            }
        });

        // ACTUALIZAR ESTADÍSTICAS DEL ENCABEZADO
        function updateHeaderStats() {
            const totalMachines = Object.keys(machines).length;
            const runningMachines = Object.values(machines).filter(m => m.status === 'running').length;
            const totalDowntime = Object.values(machines).reduce((sum, m) => sum + m.totalDowntime, 0) / 3600;
            
            const avgAvailability = Object.values(machines).reduce((sum, m) => sum + m.availability, 0) / totalMachines;
            
            document.getElementById('overallAvailability').textContent = `${avgAvailability.toFixed(1)}%`;
            document.getElementById('activeMachines').textContent = `${runningMachines}/${totalMachines}`;
            document.getElementById('monthlyDowntime').textContent = `${totalDowntime.toFixed(1)}h`;
        }

        // RENDERIZAR GRÁFICO PARETO
        function renderParetoChart() {
            const container = document.getElementById('paretoChart');
            if (!container) return;
            
            // En producción, esto vendría de SharePoint
            const topMachines = [
                { machineName: 'Fresadora 1', area: 'corte', downtime: 45.5 },
                { machineName: 'Laser 3015', area: 'sheetmetal', downtime: 38.2 },
                { machineName: 'Miller 3', area: 'soldadura', downtime: 32.7 },
                { machineName: 'Fadal 2', area: 'cnc', downtime: 28.9 },
                { machineName: 'Roladora 1', area: 'rolado', downtime: 24.3 }
            ];
            
            const maxDowntime = Math.max(...topMachines.map(m => m.downtime));
            
            container.innerHTML = topMachines.map((machine, index) => `
                <div class="pareto-item">
                    <div class="pareto-rank">#${index + 1}</div>
                    <div class="pareto-info">
                        <div class="pareto-machine">${machine.machineName}</div>
                        <div class="pareto-area">${areaNames[machine.area] || machine.area}</div>
                    </div>
                    <div class="pareto-bar-container">
                        <div class="pareto-bar">
                            <div class="pareto-fill" style="width: ${(machine.downtime / maxDowntime) * 100}%"></div>
                        </div>
                    </div>
                    <div class="pareto-time">${machine.downtime.toFixed(1)}h</div>
                </div>
            `).join('');
        }

        // RELOJ EN TIEMPO REAL
        function startLiveClock() {
            function updateClock() {
                const now = new Date();
                
                document.getElementById('liveTime').textContent = 
                    now.toLocaleTimeString('es-ES', { 
                        hour: '2-digit', 
                        minute: '2-digit', 
                        second: '2-digit',
                        hour12: false 
                    });
                
                document.getElementById('liveDate').textContent = 
                    now.toLocaleDateString('es-ES', { 
                        weekday: 'long',
                        year: 'numeric',
                        month: 'long',
                        day: 'numeric'
                    }).toUpperCase();
                
                const weekNumber = getWeekNumber(now);
                const dayOfWeek = now.getDay() || 7;
                const dayNames = ['DOMINGO', 'LUNES', 'MARTES', 'MIÉRCOLES', 'JUEVES', 'VIERNES', 'SÁBADO'];
                
                document.getElementById('weekSystem').textContent = 
                    `W${weekNumber}.${dayOfWeek} - SEMANA ${weekNumber} ${dayNames[now.getDay()]}`;
            }
            
            updateClock();
            setInterval(updateClock, 1000);
        }

        // CALCULAR NÚMERO DE SEMANA
        function getWeekNumber(date) {
            const firstDayOfYear = new Date(date.getFullYear(), 0, 1);
            const pastDaysOfYear = (date - firstDayOfYear) / 86400000;
            return Math.ceil((pastDaysOfYear + firstDayOfYear.getDay() + 1) / 7);
        }

        // CERRAR MODALES AL HACER CLIC FUERA
        window.addEventListener('click', function(e) {
            const stopModal = document.getElementById('stopModal');
            const runModal = document.getElementById('runModal');
            
            if (e.target === stopModal) {
                closeStopModal();
            }
            if (e.target === runModal) {
                closeRunModal();
            }
        });

        // SIMULAR CARGA DESDE SHAREPOINT
        async function loadMachinesFromSharePoint() {
            return new Promise(resolve => {
                setTimeout(() => {
                    console.log('Máquinas cargadas desde SharePoint');
                    resolve();
                }, 500);
            });
        }

        async function loadRecordsFromSharePoint() {
            return new Promise(resolve => {
                setTimeout(() => {
                    console.log('Registros cargados desde SharePoint');
                    resolve();
                }, 500);
            });
        }

        // GUARDAR EN SHAREPOINT
        async function saveToSharePoint(listName, data) {
            console.log(`Guardando en ${listName}:`, data);
            return new Promise(resolve => {
                setTimeout(() => {
                    console.log('Datos guardados en SharePoint');
                    resolve({ id: Date.now().toString() });
                }, 500);
            });
        }

        // CARGAR DATOS INICIALES DESDE SHAREPOINT
        async function loadInitialData() {
            try {
                await loadMachinesFromSharePoint();
                await loadRecordsFromSharePoint();
                
                updateHeaderStats();
                renderParetoChart();
            } catch (error) {
                console.error('Error cargando datos:', error);
            }
        }

        // INICIALIZAR AL CARGAR LA PÁGINA
        document.addEventListener('DOMContentLoaded', function() {
            initializeSystem();
        });
    </script>
<!-- Version: 1.1 - Fixed cache issues -->
</body>
</html>
