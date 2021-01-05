---
title: Domande frequenti sul debug di snapshot | Microsoft Docs
description: Esaminare un elenco di domande frequenti (FAQ) che potrebbero essere rilevate durante il debug di applicazioni Azure attive usando il Snapshot Debugger in Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/07/2017
ms.topic: reference
helpviewer_keywords:
- debugger
ms.assetid: 944f1eb0-a74b-4d28-ae2b-a370cd869add
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5276127f0d6755b9fdabdfa965b5c1b8c4d94823
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2020
ms.locfileid: "97727203"
---
# <a name="frequently-asked-questions-for-snapshot-debugging-in-visual-studio"></a>Domande frequenti per il debug di snapshot in Visual Studio

Ecco un elenco di domande che potrebbero sorgere durante il debug di applicazioni di Azure attive con Snapshot Debugger.

#### <a name="what-is-the-performance-cost-of-taking-a-snapshot"></a>Qual è l'impatto sulle prestazioni della creazione di uno snapshot?

Quando Snapshot Debugger acquisisce uno snapshot dell'app, crea una copia tramite fork del processo dell'app e sospende la copia creata tramite fork. Quando si esegue il debug di uno snapshot, si esegue il debug della la copia creata tramite fork del processo. Questo processo richiede solo 10-20 millisecondi, ma non copia l'heap completo dell'app. Viene invece copiata solo la tabella della pagina e le pagine vengono impostate per la copia su scrittura. Se alcuni degli oggetti dell'app nell'heap cambiano, vengono copiate le pagine corrispondenti. Questo è il motivo per cui ogni snapshot ha un costo ridotto a livello di memoria, nell'ordine di centinaia di kilobyte per la maggior parte delle app.

#### <a name="what-happens-if-i-have-a-scaled-out-azure-app-service-multiple-instances-of-my-app"></a>Cosa accade in presenza di un servizio app di Azure con scale-out (più istanze dell'app)?

In presenza di più istanze dell'app, a ogni singola istanza vengono applicati punti di acquisizione snapshot. Solo il primo punto di acquisizione snapshot da raggiungere con le condizioni specificate crea uno snapshot. Se esistono più punti di acquisizione snapshot, gli snapshot successivi provengono dalla stessa istanza che ha creato il primo snapshot. I punti di inserimento istruzione di registrazione inviati alla finestra di output visualizzeranno solo i messaggi da un'istanza, mentre i punti di inserimento istruzione di registrazione inviati ai registri applicazioni inviano messaggi da ogni istanza.

#### <a name="how-does-the-snapshot-debugger-load-symbols"></a>In che modo Snapshot Debugger carica i simboli?

Snapshot Debugger richiede di avere a disposizione i simboli corrispondenti per l'applicazione in locale o distribuiti nel servizio app di Azure. (PDB Embedded non sono attualmente supportati). Il Snapshot Debugger Scarica automaticamente i simboli dal servizio app Azure. A partire da Visual Studio 2017 versione 15.2, la distribuzione nel servizio app di Azure consente di distribuire anche i simboli dell'app.

#### <a name="does-the-snapshot-debugger-work-against-release-builds-of-my-application"></a>Snapshot Debugger funziona sulle build di versione dell'applicazione?

Sì, Snapshot Debugger è progettato per funzionare sulle build di versione. Quando si inserisce un punto di acquisizione snapshot in una funzione, la funzione viene ricompilata come versione di debug, rendendo possibile il debug. Con l'arresto di Snapshot Debugger, per le funzioni viene ripristinata la versione della build di versione.

#### <a name="can-logpoints-cause-side-effects-in-my-production-application"></a>I punti di inserimento istruzione di registrazione possono avere effetti collaterali nell'applicazione di produzione?

No, eventuali messaggi di log aggiunti all'app vengono valutati in modo virtuale e non determinano effetti collaterali nell'applicazione. Tuttavia, alcune proprietà native potrebbero non essere accessibili con i punti di inserimento istruzione di registrazione.

#### <a name="does-the-snapshot-debugger-work-if-my-server-is-under-load"></a>Se il server è sottoposto a carichi elevati, Snapshot Debugger funziona correttamente?

Sì, il debug di snapshot può funzionare nei server in condizioni di carico elevato. Snapshot Debugger limita il carico di lavoro e non acquisisce snapshot nelle situazioni in cui è presente una quantità scarsa di memoria libera nel server.

#### <a name="how-do-i-uninstall-the-snapshot-debugger"></a>Qual è la procedura per disinstallare Snapshot Debugger?

È possibile disinstallare l'estensione del sito Snapshot Debugger nel servizio app seguendo questa procedura:

1. Disattivare il servizio app tramite il Cloud Explorer in Visual Studio o nel portale di Azure.
1. Passare al sito di Kudu del servizio app (ovvero, servizioapp.**scm**.azurewebsites.net) e passare a **Estensioni del sito**.
1. Fare clic sulla X per l'estensione del sito Snapshot Debugger per rimuoverla.

#### <a name="why-are-ports-opened-during-a-snapshot-debugger-session"></a>Per quale motivo vengono aperte delle porte durante una sessione di Snapshot Debugger?

Snapshot Debugger deve aprire un set di porte per eseguire il debug degli snapshot creati in Azure. Si tratta delle stesse porte necessarie per il debug remoto. [È possibile trovare l'elenco delle porte qui](../debugger/remote-debugger-port-assignments.md).

#### <a name="how-do-i-disable-the-remote-debugger-extension"></a>Ricerca per categorie disabilitare l'estensione del debugger remoto?

Per i servizi app:
1. Disabilitare l'estensione del debugger remoto tramite il portale di Azure per il servizio app.
2. Portale di Azure > il pannello della risorsa del servizio applicazione > *le impostazioni dell'applicazione*
3. Passare alla sezione *debug* e fare clic sul pulsante *off* per il *debug remoto*.

Per AKS:
1. Aggiornare il Dockerfile per rimuovere le sezioni corrispondenti al [Visual Studio snapshot debugger nelle immagini Docker](https://github.com/Microsoft/vssnapshotdebugger-docker).
2. Ricompilare e ridistribuire l'immagine Docker modificata.

Per i set di scalabilità di macchine virtuali/macchine virtuali rimuovere l'estensione del debugger remoto, i certificati, gli insiemi di credenziali delle credenziali e i pool NAT in ingresso come segue:

1. Rimuovi estensione debugger remoto

   Esistono diversi modi per disabilitare il debugger remoto per le macchine virtuali e i set di scalabilità di macchine virtuali:

      - Disabilitare il debugger remoto tramite Cloud Explorer

         - Cloud Explorer > la risorsa della macchina virtuale > disabilitare il debug (la disabilitazione del debug non esiste per il set di scalabilità di macchine virtuali in Cloud Explorer).

      - Disabilitare il debugger remoto con script/cmdlet di PowerShell

         Per la macchina virtuale:

         ```powershell
         Remove-AzVMExtension -ResourceGroupName $rgName -VMName $vmName -Name Microsoft.VisualStudio.Azure.RemoteDebug.VSRemoteDebugger
         ```

         Per i set di scalabilità di macchine virtuali:

         ```powershell
         $vmss = Get-AzVmss -ResourceGroupName $rgName -VMScaleSetName $vmssName
         $extension = $vmss.VirtualMachineProfile.ExtensionProfile.Extensions | Where {$_.Name.StartsWith('VsDebuggerService')} | Select -ExpandProperty Name
         Remove-AzVmssExtension -VirtualMachineScaleSet $vmss -Name $extension
         ```

      - Disabilitare il debugger remoto tramite il portale di Azure
         - Portale di Azure > il pannello della risorsa macchina virtuale/set di scalabilità di macchine virtuali > estensioni
         - Disinstallare l'estensione Microsoft. VisualStudio. Azure. RemoteDebug. VSRemoteDebugger

         > [!NOTE]
         > Set di scalabilità di macchine virtuali: il portale non consente di rimuovere le porte DebuggerListener. Sarà necessario usare Azure PowerShell. Vedere di seguito per altri dettagli.

2. Rimuovere i certificati e l'insieme di credenziali delle credenziali di Azure

   Quando si installa l'estensione del debugger remoto per la macchina virtuale o i set di scalabilità di macchine virtuali, vengono creati i certificati client e server per autenticare il client di Visual Studio con le risorse della macchina virtuale di Azure o dei set di scalabilità di macchine virtuali.

   - Certificato client

      Questo certificato è un certificato autofirmato che si trova in cert:/CurrentUser/My/

      ```
      Thumbprint                                Subject
      ----------                                -------

      1234123412341234123412341234123412341234  CN=ResourceName
      ```

      Un modo per rimuovere questo certificato dal computer è tramite PowerShell

      ```powershell
      $ResourceName = 'ResourceName' # from above
      Get-ChildItem -Path Cert:\CurrentUser\My | Where-Object {$_.Subject -match $ResourceName} | Remove-Item
      ```

   - Certificato del server
      - L'identificazione personale del certificato server corrispondente viene distribuita come chiave privata nell'insieme di credenziali delle credenziali di Azure. Visual Studio tenterà di trovare o creare un insieme di credenziali delle credenziali con prefisso MSVSAZ * nell'area corrispondente alla risorsa della macchina virtuale o dei set di scalabilità di macchine virtuali. Tutte le risorse della macchina virtuale o del set di scalabilità di macchine virtuali distribuite in tale area condividono pertanto lo stesso insieme di credenziali delle credenziali.
      - Per eliminare il segreto di identificazione personale del certificato del server, passare alla portale di Azure e trovare l'insieme di credenziali delle MSVSAZ * nella stessa area in cui è ospitata la risorsa. Elimina il segreto che dovrebbe essere etichettato `remotedebugcert<<ResourceName>>`
      - Sarà anche necessario eliminare il segreto server dalla risorsa tramite PowerShell.

      Per le macchine virtuali:

      ```powershell
      $vm.OSProfile.Secrets[0].VaultCertificates.Clear()
      Update-AzVM -ResourceGroupName $rgName -VM $vm
      ```

      Per i set di scalabilità di macchine virtuali:

      ```powershell
      $vmss.VirtualMachineProfile.OsProfile.Secrets[0].VaultCertificates.Clear()
      Update-AzVmss -ResourceGroupName $rgName -VMScaleSetName $vmssName -VirtualMachineScaleSet $vmss
      ```

3. Rimuovi tutti i pool NAT in ingresso DebuggerListener (solo set di scalabilità di macchine virtuali)

   Il debugger remoto introduce i pool NAT in ingresso DebuggerListener che vengono applicati al servizio di bilanciamento del carico del servizio di scalabilità.

   ```powershell
   $inboundNatPools = $vmss.VirtualMachineProfile.NetworkProfile.NetworkInterfaceConfigurations.IpConfigurations.LoadBalancerInboundNatPools
   $inboundNatPools.RemoveAll({ param($pool) $pool.Id.Contains('inboundNatPools/DebuggerListenerNatPool-') }) | Out-Null

   if ($LoadBalancerName)
   {
      $lb = Get-AzLoadBalancer -ResourceGroupName $ResourceGroup -name $LoadBalancerName
      $lb.FrontendIpConfigurations[0].InboundNatPools.RemoveAll({ param($pool) $pool.Id.Contains('inboundNatPools/DebuggerListenerNatPool-') }) | Out-Null
      Set-AzLoadBalancer -LoadBalancer $lb
   }
   ```

#### <a name="how-do-i-disable-snapshot-debugger"></a>Ricerca per categorie disabilitare Snapshot Debugger?

Per il servizio app:
1. Disabilitare Snapshot Debugger tramite la portale di Azure per il servizio app.
2. Portale di Azure > il pannello della risorsa del servizio applicazione > *le impostazioni dell'applicazione*
3. Eliminare le impostazioni dell'app seguenti nel portale di Azure e salvare le modifiche.
   - INSTRUMENTATIONENGINE_EXTENSION_VERSION
   - SNAPSHOTDEBUGGER_EXTENSION_VERSION

   > [!WARNING]
   > Tutte le modifiche apportate alle impostazioni dell'applicazione avvierà il riavvio di un'app. Per altre informazioni sulle impostazioni dell'applicazione, vedere [configurare un'app del servizio app nel portale di Azure](/azure/app-service/web-sites-configure).

Per AKS:
1. Aggiornare il Dockerfile per rimuovere le sezioni corrispondenti al [Visual Studio snapshot debugger nelle immagini Docker](https://github.com/Microsoft/vssnapshotdebugger-docker).
2. Ricompilare e ridistribuire l'immagine Docker modificata.

Per i set di scalabilità di macchine virtuali/macchine virtuali:

Esistono diversi modi per disabilitare la Snapshot Debugger:
- Cloud Explorer > la risorsa della macchina virtuale o del set di scalabilità di macchine virtuali > disabilitare la diagnostica

- Portale di Azure > il pannello della risorsa macchina virtuale/set di scalabilità di macchine virtuali > estensioni > disinstallare Microsoft. Insights. VMDiagnosticsSettings

- Cmdlet di PowerShell da [AZ PowerShell](/powershell/azure/overview)

   Macchina virtuale:

   ```powershell
      Remove-AzVMExtension -ResourceGroupName $rgName -VMName $vmName -Name Microsoft.Insights.VMDiagnosticsSettings
   ```

   Set di scalabilità di macchine virtuali:

   ```powershell
      $vmss = Get-AzVmss -ResourceGroupName $rgName -VMScaleSetName $vmssName
      Remove-AzVmssExtension -VirtualMachineScaleSet $vmss -Name Microsoft.Insights.VMDiagnosticsSettings
   ```

## <a name="see-also"></a>Vedi anche

- [Debug in Visual Studio](../debugger/index.yml)
- [Eseguire il debug di app ASP.NET attive con Snapshot Debugger](../debugger/debug-live-azure-applications.md)
- [Eseguire il debug dei set di scalabilità di macchine virtuali ASP.NET Snapshot Debugger di Azure in Live](../debugger/debug-live-azure-virtual-machines.md)
- [Eseguire il debug di servizi Azure Kubernetes ASP.NET attivi con Snapshot Debugger](../debugger/debug-live-azure-kubernetes.md)
- [Risoluzione dei problemi e problemi noti per il debug di snapshot](../debugger/debug-live-azure-apps-troubleshooting.md)
