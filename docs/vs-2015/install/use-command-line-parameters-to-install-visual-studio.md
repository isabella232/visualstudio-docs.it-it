---
title: Usare i parametri della riga di comando per installare Visual Studio 2015 | Microsoft Docs
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-install
ms.topic: conceptual
f1_keywords:
- command-line parameters
- switches
- command prompt
ms.assetid: 480f3cb4-d873-434e-a8bf-82cff7401cf2
caps.latest.revision: 10
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: a3fe0233f08f33535be4b02cc06c29d919d75169
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/17/2019
ms.locfileid: "59651163"
---
# <a name="use-command-line-parameters-to-install-visual-studio"></a>Usare i parametri della riga di comando per installare Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Per la documentazione più recente di Visual Studio, vedere [usare i parametri della riga di comando per installare Visual Studio](/visualstudio/install/use-command-line-parameters-to-install-visual-studio).

Quando si installa Visual Studio 2015 da un prompt dei comandi è possibile usare i seguenti parametri della riga di comando, chiamati anche opzioni.

> [!NOTE]
> Assicurarsi di usare il programma di installazione effettivo e non il file di programma di avvio automatico. Ad esempio, assicurarsi che usi **`vs_enterprise.exe`** anziché vs_enterprise_*GUID*.exe. È possibile scaricare un programma di installazione dal [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015).

## <a name="list-of-command-line-parameters"></a>Elenco dei parametri della riga di comando

Per i parametri della riga di comando di Visual Studio non si fa distinzione tra maiuscole e minuscole.

|Parametro|Descrizione|
|---------------|-----------------|
|**/?**<br /><br /> **/help**<br /><br /> **/h**|Visualizza i parametri della riga di comando.|
|**/AddRemoveFeatures**|Specifica le funzionalità da aggiungere o rimuovere dal prodotto installato.|
|**/AdminFile** *AdminDeployment.xml*|Installa Visual Studio tramite il file di dati specificato per l'installazione amministrativa.|
|**/ChainingPackage** *BundleName*|Specifica quale bundle è concatenato a questo bundle. Può anche essere usato per specificare una coorte nel programma Analisi utilizzo software.|
|**/CreateAdminFile \<filename>**|Specifica il percorso per creare un file di controllo che può essere usato con /AdminFile|
|**/CustomInstallPath** *InstallationDirectory*|Installa tutti i pacchetti con destinazione modificabile nella directory specificata.|
|**/ForceRestart**|Riavvia sempre il computer dopo l'installazione.|
|**/full**|Installa tutte le funzionalità del prodotto.|
|**/Installselectableitems \<nome dell'elemento 1 > [;\< nome dell'elemento 2 >]**|Elenco di elementi dell'albero per la selezione da controllare nella schermata di selezione dell'installazione guidata.|
|**/l**<br /><br /> **/ Accedere** *nomefile*|Specifica un percorso per il file di log.|
|**/layout** *Directory*|Copia i file sul supporto di installazione nella directory specificata.|
|**/NoCacheOnlyMode**|Impedisce il prepopolamento della cache del pacchetto.|
|**/NoRefresh**|Impedisce il controllo nelle versioni più recenti di questo prodotto della disponibilità di versioni aggiornate richieste o consigliate.|
|**/norestart**|Impedisce il riavvio dell'applicazione di installazione dal computer durante o dopo l'installazione. Per i codici restituiti da cercare, vedere la sezione della [Guida per l'amministratore di Visual Studio](../install/visual-studio-administrator-guide.md).|
|**/noweb**|Impedisce l'installazione da Internet.|
|**/Overridefeeduri \<percorso file del feed >**|Percorso di un feed esterno locale che descrive gli elementi software|
|**/ProductKey**<br /><br /> *ProductKey*|Imposta un codice Product Key personalizzato che non includa trattini e non contenga più di 25 caratteri.|
|**/PromptRestart**|Richiede una conferma all'utente prima di riavviare il computer.|
|**/q**<br /><br /> **/quiet**<br /><br /> **/s**<br /><br /> **/silent**|Elimina l'interfaccia utente (UI) per l'applicazione di installazione. Se Visual Studio è già installato e non vengono specificati altri parametri tranne questo, l'applicazione di installazione viene eseguita in modalità di manutenzione.|
|**/qb**<br /><br /> **/passive**|Mostra l'avanzamento ma non attende l'input dell'utente.|
|**/repair**|Ripristina Visual Studio.|
|**/SuppressRefreshPrompt**|Impedisce la visualizzazione della finestra di dialogo che informa della disponibilità dell'aggiornamento. In tal modo, l'installazione guidata accetterà automaticamente eventuali versioni aggiornate richieste o consigliate.|
|**/u**<br /><br /> **/Uninstall**|Disinstalla [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].|
|**/Uninstall /Force**<br /><br /> **/u /force**|Disinstalla Visual Studio e tutte le funzionalità condivise con altri prodotti. **Avviso:**  Se si usa questo parametro, altri prodotti installati nello stesso computer potrebbero smettere di funzionare correttamente.|

## <a name="see-also"></a>Vedere anche

- [Guida di Visual Studio Administrator](../install/visual-studio-administrator-guide.md)