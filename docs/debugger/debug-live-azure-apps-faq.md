---
title: Domande frequenti sul debug di snapshot | Microsoft Docs
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
ms.openlocfilehash: 315b24d384a1e3576af6590923c0e546785918ae
ms.sourcegitcommit: b468d71052a1b8a697f477ab23a3644de139f1e9
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2019
ms.locfileid: "67255986"
---
# <a name="frequently-asked-questions-for-snapshot-debugging-in-visual-studio"></a>Domande frequenti per il debug di snapshot in Visual Studio

Ecco un elenco di domande che potrebbero sorgere durante il debug di applicazioni di Azure attive con Snapshot Debugger.

#### <a name="what-is-the-performance-cost-of-taking-a-snapshot"></a>Qual è l'impatto sulle prestazioni della creazione di uno snapshot?

Quando Snapshot Debugger acquisisce uno snapshot dell'app, crea una copia tramite fork del processo dell'app e sospende la copia creata tramite fork. Quando si esegue il debug di uno snapshot, si esegue il debug della la copia creata tramite fork del processo. Questo processo richiede solo 10-20 millisecondi, ma non copia l'heap completo dell'app. Viene invece copiata solo la tabella della pagina e le pagine vengono impostate per la copia su scrittura. Se alcuni degli oggetti dell'app nell'heap cambiano, vengono copiate le pagine corrispondenti. Questo è il motivo per cui ogni snapshot ha un costo ridotto a livello di memoria, nell'ordine di centinaia di kilobyte per la maggior parte delle app.

#### <a name="what-happens-if-i-have-a-scaled-out-azure-app-service-multiple-instances-of-my-app"></a>Cosa accade in presenza di un servizio app di Azure con scale-out (più istanze dell'app)?

In presenza di più istanze dell'app, a ogni singola istanza vengono applicati punti di acquisizione snapshot. Solo il primo punto di acquisizione snapshot da raggiungere con le condizioni specificate crea uno snapshot. Se esistono più punti di acquisizione snapshot, gli snapshot successivi provengono dalla stessa istanza che ha creato il primo snapshot. I punti di inserimento istruzione di registrazione inviati alla finestra di output visualizzeranno solo i messaggi da un'istanza, mentre i punti di inserimento istruzione di registrazione inviati ai registri applicazioni inviano messaggi da ogni istanza.

#### <a name="how-does-the-snapshot-debugger-load-symbols"></a>In che modo Snapshot Debugger carica i simboli?

Snapshot Debugger richiede di avere a disposizione i simboli corrispondenti per l'applicazione in locale o distribuiti nel servizio app di Azure. (Non sono attualmente supportati PDB incorporati.) Snapshot Debugger scarica automaticamente i simboli dal servizio app di Azure. A partire da Visual Studio 2017 versione 15.2, la distribuzione nel servizio app di Azure consente di distribuire anche i simboli dell'app.

#### <a name="does-the-snapshot-debugger-work-against-release-builds-of-my-application"></a>Snapshot Debugger funziona sulle build di versione dell'applicazione?

Sì, Snapshot Debugger è progettato per funzionare sulle build di versione. Quando si inserisce un punto di acquisizione snapshot in una funzione, la funzione viene ricompilata come versione di debug, rendendo possibile il debug. Con l'arresto di Snapshot Debugger, per le funzioni viene ripristinata la versione della build di versione.

#### <a name="can-logpoints-cause-side-effects-in-my-production-application"></a>I punti di inserimento istruzione di registrazione possono avere effetti collaterali nell'applicazione di produzione?

No, eventuali messaggi di log aggiunti all'app vengono valutati in modo virtuale e non determinano effetti collaterali nell'applicazione. Tuttavia, alcune proprietà native potrebbero non essere accessibili con i punti di inserimento istruzione di registrazione.

#### <a name="does-the-snapshot-debugger-work-if-my-server-is-under-load"></a>Se il server è sottoposto a carichi elevati, Snapshot Debugger funziona correttamente?

Sì, il debug di snapshot può funzionare nei server in condizioni di carico elevato. Snapshot Debugger limita il carico di lavoro e non acquisisce snapshot nelle situazioni in cui è presente una quantità scarsa di memoria libera nel server.

#### <a name="how-do-i-uninstall-the-snapshot-debugger"></a>Qual è la procedura per disinstallare Snapshot Debugger?

È possibile disinstallare l'estensione del sito Snapshot Debugger nel servizio app seguendo questa procedura:

1. Disattivare il servizio App tramite il portale di Azure o in Visual Studio Cloud Explorer.
1. Passare al sito di Kudu del servizio app (ovvero, servizioapp.**scm**.azurewebsites.net) e passare a **Estensioni del sito**.
1. Fare clic sulla X per l'estensione del sito Snapshot Debugger per rimuoverla.

#### <a name="why-are-ports-opened-during-a-snapshot-debugger-session"></a>Per quale motivo vengono aperte delle porte durante una sessione di Snapshot Debugger?

Snapshot Debugger deve aprire un set di porte per eseguire il debug degli snapshot creati in Azure. Si tratta delle stesse porte necessarie per il debug remoto. [È possibile trovare l'elenco delle porte qui](../debugger/remote-debugger-port-assignments.md).

#### <a name="how-do-i-disable-the-remote-debugger-extension"></a>Come si disabilita l'estensione del Debugger remoto?

Per i servizi App:
1. Disabilitare l'estensione del Debugger remoto tramite il portale di Azure per il servizio App.
2. Portale di Azure > Pannello di risorse del servizio dell'applicazione > *le impostazioni dell'applicazione*
3. Passare al *debug* sezione e fare clic sul *Off* pulsante *debug remoto*.

Per servizio contenitore di AZURE:
1. Aggiornare il Dockerfile per rimuovere le sezioni relative ai [Visual Studio Snapshot Debugger in immagini Docker](https://github.com/Microsoft/vssnapshotdebugger-docker).
2. Ricompilare e ridistribuire l'immagine Docker modificata.

Per la scalabilità di macchine virtuali/macchina virtuale di set di rimuovere i pool NAT in ingresso e KeyVaults di estensione, certificati, Debugger remoto come indicato di seguito:

1. Rimuovere l'estensione del Debugger remoto  

   Esistono diversi modi per disabilitare il Debugger remoto per macchine virtuali e set di scalabilità di macchine virtuali:  

      - Disabilitare il Debugger remoto tramite Cloud Explorer  

         - Cloud Explorer > risorsa di macchina virtuale > Disabilita debug (disabilitazione di debug non esiste per la scalabilità di macchine virtuali impostato in Cloud Explorer).  


      - Disabilitare il Debugger remoto con gli script o cmdlet di PowerShell  

         Per la macchina virtuale:  

         ```
         Remove-AzVMExtension -ResourceGroupName $rgName -VMName $vmName -Name Microsoft.VisualStudio.Azure.RemoteDebug.VSRemoteDebugger  
         ```

         Per set di scalabilità di macchine virtuali:  
         ```
         $vmss = Get-AzVmss -ResourceGroupName $rgName -VMScaleSetName $vmssName  
         $extension = $vmss.VirtualMachineProfile.ExtensionProfile.Extensions | Where {$_.Name.StartsWith('VsDebuggerService')} | Select -ExpandProperty Name  
         Remove-AzVmssExtension -VirtualMachineScaleSet $vmss -Name $extension  
         ```

      - Disabilitare il Debugger remoto tramite il portale di Azure
         - Portale di Azure > di scalabilità di macchine virtuali/macchine virtuali imposta pannello della risorsa > estensioni  
         - Disinstallare l'estensione Microsoft.VisualStudio.Azure.RemoteDebug.VSRemoteDebugger  


         > [!NOTE]
         > Set di scalabilità di macchine virtuali - portale non consente di rimuovere le porte DebuggerListener. È necessario usare Azure PowerShell. Di seguito sono riportate informazioni dettagliate.
  
2. Rimuovere i certificati e Azure Key Vault

   Quando si installa l'estensione del Debugger remoto per la macchina virtuale o un set di scalabilità di macchine virtuali, i certificati client e server vengono creati per autenticare il client di Visual Studio con la macchina virtuale di Azure/set di scalabilità di macchine virtuali alle risorse.  

   - Il certificato Client  

      Questo certificato è un certificato autofirmato che si trova nell'archivio certificati: / CurrentUser/My /  

      ```
      Thumbprint                                Subject  
      ----------                                -------  

      1234123412341234123412341234123412341234  CN=ResourceName  
      ```

      È un modo per rimuovere il certificato dal computer tramite PowerShell

      ```
      $ResourceName = 'ResourceName' # from above  
      Get-ChildItem -Path Cert:\CurrentUser\My | Where-Object {$_.Subject -match $ResourceName} | Remove-Item  
      ```

   - Il certificato del Server
      - L'identificazione personale certificato del server corrispondente viene distribuita come un segreto nell'insieme di credenziali di Azure. Visual Studio proverà a trovare o creare un Key Vault con prefisso MSVSAZ * nell'area corrispondente alla macchina virtuale o risorsa set di scalabilità di macchine virtuali. Set di scalabilità di macchine virtuali o una macchina virtuale tutte le risorse distribuite in tale area condividono pertanto l'insieme di credenziali stesso.  
      - Per eliminare il segreto di identificazione personale certificato server, andare al portale di Azure e trovare l'insieme di credenziali MSVSAZ * nella stessa area che ospita la risorsa. Eliminare il segreto che debba essere contrassegnate con `remotedebugcert<<ResourceName>>`  
      - È anche necessario eliminare il segreto server dalla risorsa tramite PowerShell.  

      Per le macchine virtuali:  

      ```
      $vm.OSProfile.Secrets[0].VaultCertificates.Clear()  
      Update-AzVM -ResourceGroupName $rgName -VM $vm  
      ```
                        
      Per set di scalabilità di macchine virtuali:  

      ```
      $vmss.VirtualMachineProfile.OsProfile.Secrets[0].VaultCertificates.Clear()  
      Update-AzVmss -ResourceGroupName $rgName -VMScaleSetName $vmssName -VirtualMachineScaleSet $vmss  
      ```
                        
3. Rimuovere tutti i pool NAT in ingresso DebuggerListener (solo set di scalabilità di macchine virtuali)  

   Il Debugger remoto presenta i pool NAT in ingresso di DebuggerListener che vengono applicati al servizio di bilanciamento del carico del set di scalabilità.  

   ```
   $inboundNatPools = $vmss.VirtualMachineProfile.NetworkProfile.NetworkInterfaceConfigurations.IpConfigurations.LoadBalancerInboundNatPools  
   $inboundNatPools.RemoveAll({ param($pool) $pool.Id.Contains('inboundNatPools/DebuggerListenerNatPool-') }) | Out-Null  
                
   if ($LoadBalancerName)  
   {
      $lb = Get-AzLoadBalancer -ResourceGroupName $ResourceGroup -name $LoadBalancerName  
      $lb.FrontendIpConfigurations[0].InboundNatPools.RemoveAll({ param($pool) $pool.Id.Contains('inboundNatPools/DebuggerListenerNatPool-') }) | Out-Null  
      Set-AzLoadBalancer -LoadBalancer $lb  
   }
   ```

#### <a name="how-do-i-disable-snapshot-debugger"></a>Come si disabilita Snapshot Debugger?

Per il servizio App:
1. Disabilitare il Debugger di Snapshot tramite il portale di Azure per il servizio App.
2. Portale di Azure > Pannello di risorse del servizio dell'applicazione > *le impostazioni dell'applicazione*
3. Eliminare le impostazioni seguenti nel portale di Azure e salvare le modifiche. 
    - INSTRUMENTATIONENGINE_EXTENSION_VERSION
    - SNAPSHOTDEBUGGER_EXTENSION_VERSION

    > [!WARNING]
    > Tutte le modifiche alle impostazioni dell'applicazione verranno avviato un riavvio dell'app. Per altre informazioni sulle impostazioni dell'applicazione, vedere [configurare un'app di servizio App nel portale di Azure](/azure/app-service/web-sites-configure).

Per servizio contenitore di AZURE:
1. Aggiornare il Dockerfile per rimuovere le sezioni relative ai [Visual Studio Snapshot Debugger in immagini Docker](https://github.com/Microsoft/vssnapshotdebugger-docker).
2. Ricompilare e ridistribuire l'immagine Docker modificata.

Per set di scalabilità di macchine virtuali/macchine virtuali:

Esistono diversi modi per disabilitare il Debugger di Snapshot:
- Cloud Explorer > risorsa del set di scalabilità di macchine virtuali/macchine virtuali > disabilitare la diagnostica

- Portale di Azure > pannello della risorsa di set di scalabilità di macchine virtuali/macchine virtuali > estensioni > estensione vmdiagnosticssettings disinstallare

- I cmdlet di PowerShell da [Az PowerShell](https://docs.microsoft.com/powershell/azure/overview)

    Macchina virtuale:
    ```
        Remove-AzVMExtension -ResourceGroupName $rgName -VMName $vmName -Name Microsoft.Insights.VMDiagnosticsSettings 
    ```
    
    Set di scalabilità di macchine virtuali:
    ```
        $vmss = Get-AzVmss -ResourceGroupName $rgName -VMScaleSetName $vmssName
        Remove-AzVmssExtension -VirtualMachineScaleSet $vmss -Name Microsoft.Insights.VMDiagnosticsSettings
    ```

## <a name="see-also"></a>Vedere anche

- [Debug in Visual Studio](../debugger/index.md)
- [Il debug in tempo reale delle App ASP.NET usando il Debugger di Snapshot](../debugger/debug-live-azure-applications.md)
- [Eseguire il debug in tempo reale i set di scalabilità Machines\Virtual ASP.NET macchine virtuali usando il Debugger di Snapshot](../debugger/debug-live-azure-virtual-machines.md)
- [Eseguire il debug in tempo reale ASP.NET Azure Kubernetes con il Debugger di Snapshot](../debugger/debug-live-azure-kubernetes.md)
- [Risoluzione dei problemi e problemi noti per il debug di snapshot](../debugger/debug-live-azure-apps-troubleshooting.md)