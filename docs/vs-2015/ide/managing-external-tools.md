---
title: Gestione di strumenti esterni | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.externaltools
helpviewer_keywords:
- Create GUID tool
- RC (Resource Compiler)
- ReBase tool
- Windows NT Message Compiler
- Windows NT C++ Symbol Undecorator
- tstcon32.exe
- Type Library Generator
- Windows NT Image Binder
- tools [Visual Studio], external
- RowsetViewer tool
- utilities, external tools
- Local Test Manager
- OLE DB Rowset Viewer
- Midlc (IDL Compiler)
- ATL Trace Tool
- Odbcte32w.exe
- IDL Compiler
- HCW (Help Workshop)
- Message Compiler [Visual Studio]
- UUID Generator
- MIDL, external tools
- ErrLook tool
- MAKEHM tool
- Error lookup tool
- OLEVIEW (Object Viewer)
- Uuidgen.exe
- WebDbg tool
- OLE/COM Object Viewer
- LTM (Local Test Manager)
- ATLTraceTool.exe
- Bind tool
- Vsvars32.bat
- external tools [Visual Studio]
- ODBC Test
- Windows NT Image Rebaser
- undname.exe
- Vcspawn.exe
- ActiveX Control Test Container
- mc (Message Compiler)
- GUIDGEN tool
- Odbcte32.exe
- DisableMsg tool
- MkTypLib tool
- Help Workshop
- Resource Compiler
ms.assetid: f382fd40-a98f-4934-8c9a-5aeae881acde
caps.latest.revision: 41
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d55fdcd6da677eb34c8aee45787880781d58260a
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47531099"
---
# <a name="managing-external-tools"></a>Gestione di strumenti esterni
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [gestire strumenti esterni](https://docs.microsoft.com/visualstudio/ide/managing-external-tools).  
  
È possibile chiamare strumenti esterni direttamente in Visual Studio. Alcuni strumenti predefiniti sono disponibili nel menu **Strumenti**, ma è possibile aggiungere altri file eseguibili personalizzati.  
  
## <a name="tools-available-on-the-visual-studio-tools-menu"></a>Strumenti disponibili nel Menu Strumenti di Visual Studio  
 È possibile chiamare i seguenti strumenti dal menu **Strumenti** in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. È anche possibile chiamare gli strumenti nella finestra **Avvio veloce** usando il nome. Ad esempio, per chiamare GuidGen.exe, digitare **Crea GUID**.  
  
1.  Crea GUID: genera un GUID.  
  
2.  Ricerca errori: ottiene un messaggio di errore dal valore immesso. Per altre informazioni, vedere [Riferimenti a ERRLOOK](http://msdn.microsoft.com/library/6040ffc1-2355-4a45-8998-84cbcba4ca91).  
  
3.  Strumento di traccia ATL/MFC: mostra i messaggi di traccia di debug nelle origini ATL e MFC.  
  
4.  PreEmptive Dotfuscator e Analytics: protegge programmi .NET da attacchi di reverse engineering.  
  
5.  SPY++: mostra processi, thread, finestre e messaggi graficamente.  
  
6.  Editor configurazione servizi WCF: consente di creare e modificare le impostazioni di configurazione dei servizi WCF.  
  
> [!WARNING]
>  È possibile visualizzare un elenco diverso degli strumenti esterni, a seconda della versione di Visual Studio installata e del profilo di impostazioni applicate. Per altre informazioni, vedere [Personalizzazione delle impostazioni di sviluppo in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="adding-new-tools"></a>Aggiunta di nuovi strumenti  
 È possibile aggiungere uno strumento esterno al menu **Strumenti**. Aprire la finestra di dialogo **Strumenti esterni**, fare clic su **Aggiungi**, quindi inserire le informazioni. L'immissione seguente consente ad esempio di aprire la cartella dove si trova il file attualmente aperto in Visual Studio:  
  
1.  Titolo: Apri percorso file  
  
2.  Comando: explorer.exe  
  
3.  Argomenti: /root, "$(ItemDir)"  
  
## <a name="arguments-for-external-tools"></a>Strumenti esterni - Argomenti  
 Gli argomenti seguenti sono variabili di Visual Studio assegnate all'avvio di uno strumento esterno. I collegamenti a strumenti esterni come Notepad o Spy++ possono essere elencati nel menu **Strumenti** usando la finestra di dialogo Strumenti esterni.  
  
> [!NOTE]
>  La barra di stato dell'IDE visualizza le variabili di Riga corrente e Colonna corrente per indicare dove si trova il punto di inserimento nell'Editor codice attivo. La variabile di Testo corrente restituisce il testo o codice selezionato in quella posizione.  
  
|nome|Argomento|Descrizione|  
|----------|--------------|-----------------|  
|Percorso elemento|$(ItemPath)|Nome file completo del file corrente (unità + percorso + nome file).|  
|Directory elemento|$(ItemDir)|Directory del file corrente (unità + percorso).|  
|Nome file elemento|$(ItemFilename)|Nome del file corrente (nome file).|  
|Estensione di elemento|$(ItemExt)|Estensione del nome del file corrente.|  
|Riga corrente|$(CurLine)|Posizione della riga corrente del cursore nella finestra del codice.|  
|Colonna corrente|$(CurCol)|Posizione della colonna corrente del cursore nella finestra del codice.|  
|Testo corrente|$(CurText)|Testo selezionato.|  
|Percorso di destinazione|$(TargetPath)|Nome file completo dell'elemento da compilare (unità + percorso + nome file).|  
|Target Directory|$(TargetDir)|Directory dell'elemento da compilare.|  
|Target Name|$(TargetName)|Nome file dell'elemento da compilare.|  
|Estensione di destinazione|$(TargetExt)|Estensione di file dell'elemento da compilare.|  
|Directory binaria|$(BinDir)|Posizione finale del file binario in fase di compilazione (definita come unità + percorso). Ad esempio: **\\...\Documenti\Visual Studio \<Versione>\\<NomeProgetto\>\bin\debug**|  
|Directory del progetto|$(ProjDir)|Directory del progetto corrente (unità + percorso).|  
|Nome del file di progetto|$(ProjFileName)|Nome file del progetto corrente (unità + percorso + nome file).|  
|Directory soluzione|$(SolutionDir)|Directory della soluzione corrente (unità + percorso).|  
|Nome file della soluzione|$(SolutionFileName)|Nome file della soluzione corrente (unità + percorso + nome file).|  
  
## <a name="see-also"></a>Vedere anche  
 [Strumenti per la compilazione in C/C++](http://msdn.microsoft.com/library/48d9daf4-6bbf-473a-8ce2-bf2923b69f80)







