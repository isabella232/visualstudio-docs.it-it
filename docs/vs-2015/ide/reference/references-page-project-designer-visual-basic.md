---
title: Riferimenti (pagina), Progettazione progetti (Visual Basic) | Microsoft Docs
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
- vb.ProjectPropertiesReference
- vb.ProjectPropertiesUnusedReference
- vb.ProjectPropertiesReferencePaths
helpviewer_keywords:
- References page in Project Designer
- Project Designer, References page
- Unused References dialog box
ms.assetid: 5a47c595-e084-401c-86e1-74e0bf74fd86
caps.latest.revision: 40
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a5e89b77749b331665869393b2b3cf7e520d3371
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47528498"
---
# <a name="references-page-project-designer-visual-basic"></a>Riferimenti (pagina), Creazione progetti (Visual Basic)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [riferimenti (pagina), creazione progetti (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/references-page-project-designer-visual-basic).  
  
  
Usare la pagina **Riferimenti** di **Progettazione progetti** per gestire riferimenti, riferimenti Web e spazi dei nomi importati del progetto. I progetti possono contenere riferimenti a componenti COM, servizi Web XML, assembly o librerie di classi .NET Framework oppure altre librerie di classi. Per altre informazioni sull'uso dei riferimenti, vedere [Gestione dei riferimenti in un progetto](../../ide/managing-references-in-a-project.md).  
  
 Per accedere alla pagina **Riferimenti**, scegliere un nodo del progetto (non il nodo **Soluzione**) in **Esplora soluzioni**. Quindi scegliere **Progetto**, **Proprietà** sulla barra dei menu. Quando viene visualizzata la finestra Progettazione progetti fare clic sulla scheda **Riferimenti**.  
  
## <a name="uielement-list"></a>Elenco UIElement  
 Le opzioni seguenti consentono di selezionare o rimuovere riferimenti e spazi dei nomi importati del progetto.  
  
 **Riferimenti inutilizzati**  
 Fare clic su questo pulsante per accedere alla finestra di dialogo **Riferimenti inutilizzati**.  
  
 La finestra di dialogo **Riferimenti inutilizzati** consente di rimuovere i riferimenti inclusi nel progetto ma non usati effettivamente dal codice. Contiene una griglia in cui sono elencati **Nome riferimento**, **Percorso** e altre informazioni sui riferimenti allo spazio dei nomi inutilizzati nel progetto. Nella griglia selezionare i riferimenti allo spazio dei nomi che si vuole rimuovere dal progetto e fare clic su **Rimuovi**.  
  
 **Percorsi riferimento**  
 Fare clic su questo pulsante per accedere alla finestra di dialogo **Percorsi riferimento**.  
  
> [!NOTE]
>  Quando il sistema del progetto trova un riferimento a un assembly, il sistema risolve il riferimento eseguendo una ricerca nei percorsi seguenti nell'ordine seguente:  
>   
>  1.  Cartella del progetto. I file della cartella del progetto vengono visualizzati in **Esplora soluzioni** quando l'opzione **Mostra tutti i file** non è attiva.  
> 2.  Cartelle specificate nella finestra di dialogo **Percorsi riferimento**.  
> 3.  Cartelle che visualizzano i file nella finestra di dialogo **Aggiungi riferimento**.  
> 4.  Cartella obj del progetto. Quando si aggiunge un riferimento COM al progetto, uno o più assembly possono essere aggiunti alla cartella obj del progetto.  
  
 **Riferimenti**  
 Questo elenco visualizza tutti i riferimenti del progetto, utilizzati o inutilizzati.  
  
 **Aggiungi**  
 Fare clic su questo pulsante per aggiungere un riferimento o un riferimento Web all'elenco **Riferimenti**.  
  
 Scegliere **Riferimento** per aggiungere un riferimento al progetto tramite la finestra di dialogo Aggiungi riferimento.  
  
 Scegliere **Riferimento Web** per aggiungere un riferimento Web al progetto tramite la finestra di dialogo Aggiungi riferimento Web.  
  
 **Rimuovi**  
 Selezionare uno o più riferimenti nell'elenco **Riferimenti**, quindi fare clic su questo pulsante per eliminarli.  
  
 **Aggiorna riferimento Web**  
 Selezionare un riferimento Web nell'elenco **Riferimenti** e fare clic su questo pulsante per aggiornarlo.  
  
 **Spazi dei nomi importati**  
 È possibile digitare il proprio spazio dei nomi in questa casella e fare clic su **Aggiungi importazione utente** per aggiungerlo all'elenco degli spazi dei nomi.  
  
 È possibile creare alias per gli spazi dei nomi importati dall'utente. A tale scopo, immettere l'alias e lo spazio dei nomi nel formato *alias*=*spazio dei nomi*. Questa operazione è utile se si usano spazi dei nomi lunghi, ad esempio `Http= MyOrg.ObjectLib.Internet.WebRequestMethods.Http`.  
  
 **Aggiungi importazione utente**  
 Fare clic su questo pulsante per aggiungere lo spazio specificato nella casella **Spazi dei nomi importati** all'elenco degli spazi dei nomi importati. Il pulsante è attivo solo se lo spazio dei nomi specificato non è presente nell'elenco.  
  
 **Elenco Spazi dei nomi**  
 Questo elenco visualizza tutti gli spazi dei nomi disponibili. Le caselle di controllo per gli spazi dei nomi inclusi nel progetto sono selezionate.  
  
 **Aggiorna importazione utente**  
 Selezionare uno spazio dei nomi specificato dall'utente nell'elenco degli spazi dei nomi, digitare il nome come cui si vuole sostituirlo nella casella **Spazi dei nomi importati** e quindi fare clic su questo pulsante per impostare il nuovo spazio dei nomi. Il pulsante è attivo solo se lo spazio dei nomi selezionato è tra quelli aggiunti all'elenco mediante il pulsante **Aggiungi importazione utente**. È possibile aggiungere:  
  
-   Classi o spazi dei nomi, ad esempio <xref:System.Math?displayProperty=fullName>.  
  
-   Importazioni con alias, ad esempio `VB=Microsoft.VisualBasic`.  
  
-   Spazi dei nomi XML, ad esempio `<xmlns:xsl="http://www.w3.org/1999/XSL/Transform">`.  
  
## <a name="see-also"></a>Vedere anche  
 [NIB Procedura: Aggiungere o rimuovere riferimenti utilizzando la finestra di dialogo Aggiungi riferimento](http://msdn.microsoft.com/en-us/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)   
 [Procedura: Aggiungere o rimuovere spazi dei nomi importati (Visual Basic)](../../ide/how-to-add-or-remove-imported-namespaces-visual-basic.md)   
 [NIB: Aggiungi finestra di dialogo riferimento Web](http://msdn.microsoft.com/en-us/bdf05776-c591-40af-bfd7-e1e2aa1e87b5)   
 [Istruzione Imports (spazio dei nomi XML)](http://msdn.microsoft.com/library/1f4d50a6-08c7-4c2e-8206-ccae35fcd1b4)



