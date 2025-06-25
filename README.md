<h2 class="section-title">Import / Export Transaction</h2>

<div class="transaction-detail-view p-grid p-mt-3 p-px-3">
  <!-- LEFT: Metadata -->
  <div class="p-col-12 p-md-5 p-lg-4">
    <div class="p-card custom-card">
      <div class="p-d-flex p-ai-center p-jc-between p-mb-3">
        <div>
          <h3 class="txn-title">Edge_OFS_BEM_Txn_4</h3>
          <p-tag value="Active" severity="success" styleClass="p-mt-1 p-px-3 p-py-1"></p-tag>
        </div>
        <button pButton label="View more" class="p-button-sm p-button-outlined"></button>
      </div>

      <table class="txn-meta-table">
        <tr *ngFor="let field of transactionFields">
          <td class="label-cell">{{ field.label }}</td>
          <td class="value-cell">{{ field.value || '-' }}</td>
        </tr>
      </table>
    </div>
  </div>

  <!-- RIGHT: History Table -->
  <div class="p-col-12 p-md-7 p-lg-8">
    <div class="p-d-flex p-jc-between p-ai-center p-mb-2">
      <h4 class="table-title">Import/Export History</h4>
      <button pButton icon="pi pi-download" label="Export" class="p-button-sm p-button-secondary"></button>
    </div>

    <p-table [value]="selectedTransaction.history" class="p-datatable-sm" [responsiveLayout]="'scroll'">
      <ng-template pTemplate="header">
        <tr>
          <th></th>
          <th>Date & Time</th>
          <th>Environment</th>
          <th>Performed by</th>
          <th>Txn. Status</th>
        </tr>
      </ng-template>
      <ng-template pTemplate="body" let-tx>
        <tr>
          <td>
            <span
              class="direction-badge"
              [ngStyle]="{ 'background-color': getDirectionColor(tx.direction) }"
            ></span>
            {{ tx.direction }}
          </td>
          <td>{{ tx.dateTime | date: 'MMMM d, y @ h:mm a' }}</td>
          <td>{{ tx.environment }}</td>
          <td>{{ tx.performedBy }}</td>
          <td>
            <p-tag
              [value]="tx.status"
              [severity]="tx.status === 'Success' ? 'success' : 'danger'"
              styleClass="p-px-2 p-py-1"
            ></p-tag>
          </td>
        </tr>
      </ng-template>
    </p-table>
  </div>
</div>









export class ImportExportComponent {
  selectedTransaction = {
    transactionName: 'Edge_OFS_BEM_Txn_4',
    status: 'Active',
    version: '1.0',
    der: 'DEX19723',
    partnerName: 'Edge OFS BEM and P&C Transaction',
    partnerType: 'Client',
    clientName: 'Edge OFS BEM',
    clientDuns: '-',
    b2bFormat: 'DELEMETED',
    eftr: 'EFTR5678',
    effectiveDate: '05/27/2025',
    lastUpdated: '05/27/2025 18:12',
    history: [
      {
        direction: 'Imported',
        dateTime: new Date('2025-06-03T10:30:00'),
        environment: 'PROD',
        performedBy: 'Alice Smith',
        status: 'Success',
      },
      {
        direction: 'Exported',
        dateTime: new Date('2025-06-03T10:30:00'),
        environment: 'STG',
        performedBy: 'Alice Smith',
        status: 'Success',
      },
      {
        direction: 'Exported',
        dateTime: new Date('2025-06-04T10:30:00'),
        environment: 'PROD',
        performedBy: 'Johannesberg Smith',
        status: 'Failed',
      },
      {
        direction: 'Exported',
        dateTime: new Date('2025-06-05T10:30:00'),
        environment: 'PROD',
        performedBy: 'Alice Smith',
        status: 'Success',
      },
    ]
  };

  transactionFields = [
    { label: 'Version', value: this.selectedTransaction.version },
    { label: 'DER#', value: this.selectedTransaction.der },
    { label: 'Transaction Name', value: this.selectedTransaction.transactionName },
    { label: 'Partner Name', value: this.selectedTransaction.partnerName },
    { label: 'Partner Type', value: this.selectedTransaction.partnerType },
    { label: 'Client Name', value: this.selectedTransaction.clientName },
    { label: 'Client DUNS#', value: this.selectedTransaction.clientDuns },
    { label: 'B2B Format', value: this.selectedTransaction.b2bFormat },
    { label: 'EFTR #', value: this.selectedTransaction.eftr },
    { label: 'Effective Date', value: this.selectedTransaction.effectiveDate },
    { label: 'Last Updated', value: this.selectedTransaction.lastUpdated },
    { label: 'Version', value: this.selectedTransaction.version },
  ];

  getDirectionColor(direction: string): string {
    return direction === 'Imported' ? '#5CB85C' : '#0275d8';
  }
}



.section-title {
  font-size: 1.5rem;
  font-weight: 600;
  margin-bottom: 1rem;
}

.txn-title {
  font-size: 1.2rem;
  font-weight: 600;
  margin-bottom: 0.2rem;
}

.custom-card {
  border: 1px solid #dee2e6;
  border-radius: 6px;
  padding: 1rem;
}

.txn-meta-table {
  width: 100%;
  border-collapse: collapse;

  td {
    padding: 0.4rem 0.6rem;
    vertical-align: top;
  }

  .label-cell {
    font-weight: bold;
    background: #e9ecef;
    width: 40%;
  }

  .value-cell {
    background: #f8f9fa;
    width: 60%;
  }
}

.table-title {
  font-size: 1.1rem;
  font-weight: 600;
}

.direction-badge {
  display: inline-block;
  width: 5px;
  height: 100%;
  margin-right: 6px;
  border-radius: 2px;
}




