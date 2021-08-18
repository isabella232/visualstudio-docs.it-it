---
title: Comando CodeIndex
description: Informazioni su come usare il comando CodeIndex per gestire l'indicizzazione del codice Azure DevOps Server (noto in precedenza come Team Foundation Server ).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- command-line tools [Team Foundation Server]
- TFSConfig
- CodeIndex command [Team Foundation Server]
ms.assetid: b79568d4-6a64-4ca9-a1ee-3e57f92a9c5c
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: a16d1ec94ad958f7a93b061c23650148fe38398d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122056329"
---
# <a name="codeindex-command"></a>Comando CodeIndex

Usare il comando **CodeIndex** per gestire l'indicizzazione del codice in Team Foundation Server. Ad esempio, è possibile che si desideri reimpostare l'indice per correggere le informazioni di CodeLens o disabilitare l'indicizzazione per esaminare eventuali problemi di prestazioni del server.

## <a name="required-permissions"></a>Autorizzazioni necessarie

Per usare il comando **CodeIndex**, è necessario essere membro del gruppo di sicurezza **Team Foundation Administrators**. Vedere [Permissions and groups in Azure DevOps and TFS](/azure/devops/organizations/security/permissions?view=vsts&preserve-view=true) (Autorizzazioni e gruppi in Azure DevOps e TFS).

> [!NOTE]
> Anche se si accede con le credenziali amministrative, per eseguire questo comando, è necessario aprire una finestra del prompt dei comandi con privilegi elevati. È inoltre necessario eseguire questo comando dal livello applicazione di Team Foundation.

## <a name="syntax"></a>Sintassi

```cmd
TFSConfig CodeIndex /indexingStatus | /setIndexing:[ on | off | keepupOnly ] | /ignoreList:[ add | remove | removeAll | view ] ServerPath | /listLargeFiles [/fileCount:FileCount] [/minSize:MinSize] | /reindexAll | /destroyCodeIndex [/noPrompt] | /temporaryDataSizeLimit:[ view | <SizeInGBs> | disable ] | /indexHistoryPeriod:[ view | all | <NumberOfMonths> ] [/collectionName:CollectionName | /collectionId:CollectionId]
```

### <a name="parameters"></a>Parametri

|**Argument**|**Descrizione**|
|------------------| - |
|`CollectionName`|Specifica il nome della raccolta di progetti. Se il nome contiene spazi, racchiuderlo tra virgolette, ad esempio, "Sito Web di Fabrikam".|
|`CollectionId`|Specifica il numero di identificazione della raccolta di progetti.|
|`ServerPath`|Specifica il percorso di un file di codice.|

|**Opzione**|**Descrizione**|
|----------------| - |
|**/indexingStatus**|Mostrare lo stato e la configurazione del servizio di indicizzazione del codice.|
|**/setIndexing:**[ on &#124; off &#124; keepupOnly ]|-   **on**: avvia l'indicizzazione di tutti gli insiemi di modifiche.<br />-   **off**: arresta l'indicizzazione di tutti gli insiemi di modifiche.<br />-   **keepupOnly**: interrompe l'indicizzazione degli insiemi di modifiche creati in precedenza e avvia l'indicizzazione solo dei nuovi insiemi di modifiche.|
|**/ignoreList:**[ add &#124; remove &#124; removeAll &#124; view ] `ServerPath`<br /><br /> È possibile usare il carattere jolly (*) all'inizio, alla fine, oppure a entrambe le estremità del percorso server.|Specifica l'elenco di file di codice e i rispettivi percorsi da non indicizzare.<br /><br /> -   **add**: aggiunge il file da non indicizzare all'elenco di file ignorati.<br />-   **remove**: rimuove il file da indicizzare dall'elenco di file ignorati.<br />-   **removeAll**: cancella l'elenco dei file ignorati e avvia l'indicizzazione di tutti i file.<br />-   **view**: visualizza tutti i file non sottoposti a indicizzazione.|
|**/listLargeFiles [/fileCount:** `FileCount` **/minSize:** `MinSize` ]|Mostra il numero specificato di file che supera la dimensione specificata in KB. È quindi possibile usare l'opzione **/ignoreList** per escludere questi file dall'indicizzazione.|
|**/reindexAll**|Cancellare i dati indicizzati in precedenza e riavviare l'indicizzazione.|
|**/destroyCodeIndex [/noPrompt]**|Eliminare l'indice del codice e rimuovere tutti i dati indicizzati. Non è richiesta conferma se si usa l'opzione **/noPrompt**.|
|**/temporaryDataSizeLimit**:[ view &#124; <`SizeInGBs`> &#124; disable ]|Controllare la quantità di dati temporanei creati da CodeLens durante l'elaborazione degli insiemi di modifiche. Il limite predefinito è 2 GB.<br /><br /> -   **view**: mostra il limite di dimensioni attuale.<br />-   `SizeInGBs`: modifica il limite di dimensioni.<br />-   **disable**: rimuove il limite di dimensioni.<br /><br /> Questo limite viene verificato prima dell'elaborazione di un nuovo insieme di modifiche con CodeLens. Se i dati temporanei superano questo limite, CodeLens sospende l'elaborazione degli insiemi di modifiche precedenti, non di quelli nuovi. CodeLens riavvia l'elaborazione dopo che i dati sono stati puliti e sono tornati sotto il limite. La pulizia viene eseguita automaticamente una volta al giorno. Questo implica che i dati temporanei potrebbero superare questo limite prima dell'esecuzione del processo di pulizia.|
|**/indexHistoryPeriod**:[ view &#124; all &#124; <`NumberOfMonths`> ]|Controllare la lunghezza dell'intervallo di indicizzazione della cronologia delle modifiche. Ciò incide sulla quantità di cronologia che CodeLens mostra all'utente. Il limite predefinito è di 12 mesi. Questo significa che CodeLens mostra la cronologia delle modifiche solo degli ultimi 12 mesi.<br /><br /> -   **view**: mostra il numero di mesi corrente.<br />-   **all**: indicizza tutta la cronologia delle modifiche.<br />-   `NumberOfMonths`: modifica il numero di mesi usato per indicizzare la cronologia delle modifiche.|
|**/collectionName:**`CollectionName`|Specifica il nome dell'insieme di progetti sulla quale eseguire il comando **CodeIndex**. Obbligatoria se non si usa **/CollectionId**.|
|**/collectionId:**`CollectionId`|Specifica il numero di identificazione dell'insieme di progetti sulla quale eseguire il comando **CodeIndex**. Obbligatoria se non si usa **/CollectionName**.|

## <a name="examples"></a>Esempio

> [!NOTE]
> Società, organizzazioni, prodotti, nomi di dominio, indirizzi di posta elettronica, logo, persone, luoghi ed eventi citati nell'esempio sono puramente immaginari.  Nessuna associazione con nessuna società, organizzazione, prodotto, nome di dominio, indirizzo di posta elettronica, logo, persona, luogo o evento è intenzionale o può essere presupposta.

Per vedere la configurazione e lo stato di indicizzazione del codice:

```cmd
TFSConfig CodeIndex /indexingStatus /collectionName:"Fabrikam Website"
```

Per avviare l'indicizzazione di tutti gli insiemi di modifiche:

```cmd
TFSConfig CodeIndex /setIndexing:on /collectionName:"Fabrikam Website"
```

Per arrestare l'indicizzazione dei set di modifiche creati in precedenza e avviare l'indicizzazione solo dei nuovi insiemi di modifiche:

```cmd
TFSConfig CodeIndex /setIndexing:keepupOnly /collectionName:"Fabrikam Website"
```

Per trovare fino a 50 file con dimensioni superiori a 10 KB:

```cmd
TFSConfig CodeIndex /listLargeFiles /fileCount:50 /minSize:10 /collectionName:"Fabrikam Website"
```

Per escludere un file specifico dall'indicizzazione e aggiungerlo all'elenco di file ignorati:

```cmd
TFSConfig CodeIndex /ignoreList:add "$/Fabrikam Website/Catalog.cs" /collectionName:"Fabrikam Website"
```

Per visualizzare tutti i file non sottoposti a indicizzazione:

```cmd
TFSConfig CodeIndex /ignoreList:view
```

Per cancellare i dati precedentemente indicizzati e riavviare l'indicizzazione:

```cmd
TFSConfig CodeIndex /reindexAll /collectionName:"Fabrikam Website"
```

Per salvare tutta la cronologia dell'insieme di modifiche:

```cmd
TFSConfig CodeIndex /indexHistoryPeriod:all /collectionName:"Fabrikam Website"
```

Per rimuovere il limite di dimensioni nei dati temporanei di CodeLens e continuare l'indicizzazione indipendentemente dalle dimensioni dei dati temporanei:

```cmd
TFSConfig CodeIndex /temporaryDataSizeLimit:disable /collectionName:"Fabrikam Website"
```

Per eliminare l'indice di codice con conferma:

```cmd
TFSConfig CodeIndex /destroyCodeIndex /collectionName:"Fabrikam Website"
```

## <a name="see-also"></a>Vedi anche

- [Trovare le modifiche apportate al codice e altri elementi della cronologia con CodeLens](../ide/find-code-changes-and-other-history-with-codelens.md)
- [Managing server configuration with TFSConfig](/azure/devops/server/command-line/tfsconfig-cmd) (Gestione della configurazione del server con TFSConfig)
