# Laboratorio 17 — Análisis y Optimización del Consumo de Recursos Cloud

FinOps: Cost Explorer, análisis de costos con Python y presupuesto AWS Budgets.

Continúa en el **Laboratorio 18** (no destruir el presupuesto al terminar este lab).

## Estructura

```
finops/
  aws-cost-sample.csv   # Dataset de ejemplo AcmeCorp
  analyze_costs.py      # Análisis con pandas
finops-budget/
  main.tf               # Presupuesto mensual $5 + IAM Budgets
  variables.tf
```

## Parte B — Análisis local

```powershell
python -m pip install pandas
cd finops
python analyze_costs.py
```

## Parte C — Presupuesto real

> El CLI de este equipo usa el usuario IAM `Ale-Cruz` (no el default `devsecops-lab-user`).

```powershell
cd finops-budget
terraform init
terraform apply -var="iam_user_name=Ale-Cruz" -var="alert_email=su-correo@ejemplo.com" -auto-approve
```

Confirmar en: **Billing and Cost Management → Budgets → `devsecops-lab-monthly-budget`**.

## Entregables

1. Captura de Cost Explorer (group by Service, últimos 3 meses).
2. Salida completa de `python analyze_costs.py`.
3. Respuestas de interpretación (desperdicio vs rightsizing, ahorro anual EBS/EIP, propuesta RDS).
4. Captura del budget en la consola de AWS.
