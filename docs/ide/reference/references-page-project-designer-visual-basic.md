---
title: Riferimenti (pagina), Creazione progetti (Visual Basic)
description: Informazioni su come usare la pagina Riferimenti di progettazione Project per gestire i riferimenti, i riferimenti Web e gli spazi dei nomi importati del progetto.
ms.custom: SEO-VS-2020
ms.date: 06/21/2017
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesReference
- vb.ProjectPropertiesUnusedReference
- vb.ProjectPropertiesReferencePaths
helpviewer_keywords:
- References page in Project Designer
- Project Designer, References page
ms.assetid: 5a47c595-e084-401c-86e1-74e0bf74fd86
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 9c56614d835da1f03c4ef44f01be8ec0493dd6b1
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122117150"
---
# <a name="references-page-project-designer-visual-basic"></a>Riferimenti (pagina), Creazione progetti (Visual Basic)

Usare la pagina **Riferimenti** di **Creazione progetti** per gestire riferimenti, riferimenti Web e spazi dei nomi importati del progetto. I progetti possono contenere riferimenti a componenti COM, servizi Web XML, assembly o librerie di classi .NET o altre librerie di classi. Per altre informazioni sull'uso dei riferimenti, vedere [Gestione dei riferimenti in un progetto](../../ide/managing-references-in-a-project.md).

Per accedere alla pagina **Riferimenti**, scegliere un nodo del progetto (non il nodo **Soluzione**) in **Esplora soluzioni**. Quindi scegliere **Progetto**, **Proprietà** sulla barra dei menu. Quando viene visualizzata la finestra Progettazione progetti fare clic sulla scheda **Riferimenti**.

## <a name="uielement-list"></a>Elenco degli elementi di interfaccia

Le opzioni seguenti consentono di selezionare o rimuovere riferimenti e spazi dei nomi importati del progetto.

**Percorsi riferimento**

Fare clic su questo pulsante per accedere alla finestra di dialogo **Percorsi riferimento**.

> [!NOTE]
> Quando il sistema del progetto trova un riferimento a un assembly, il sistema risolve il riferimento eseguendo una ricerca nei percorsi seguenti nell'ordine seguente:
>
> 1. Cartella del progetto. I file della cartella del progetto vengono visualizzati in **Esplora soluzioni** quando l'opzione **Mostra tutti i file** non è attiva.
> 2. Cartelle specificate nella finestra di dialogo **Percorsi riferimento**.
> 3. Cartelle che visualizzano i file nella finestra di dialogo **Aggiungi riferimento**.
> 4. Cartella obj del progetto. Quando si aggiunge un riferimento COM al progetto, uno o più assembly possono essere aggiunti alla cartella obj del progetto.

 **Riferimenti**

Questo elenco visualizza tutti i riferimenti del progetto, utilizzati o inutilizzati.

 **Aggiungere**

Fare clic su questo pulsante per aggiungere un riferimento o un riferimento Web all'elenco **Riferimenti**.

Scegliere **Riferimento** per aggiungere un riferimento al progetto tramite la finestra di dialogo Aggiungi riferimento.

Scegliere **Riferimento Web** per aggiungere un riferimento Web al progetto tramite la finestra di dialogo **Aggiungi riferimento Web**.

 **Rimuovi**

Selezionare uno o più riferimenti nell'elenco **Riferimenti**, quindi fare clic su questo pulsante per eliminarli.

 **Aggiorna riferimento Web**

Selezionare un riferimento Web nell'elenco **Riferimenti** e fare clic su questo pulsante per aggiornarlo.

 **Spazi dei nomi importati**

È possibile digitare il proprio spazio dei nomi in questa casella e fare clic su **Aggiungi importazione utente** per aggiungerlo all'elenco degli spazi dei nomi.

È possibile creare alias per gli spazi dei nomi importati dall'utente. A tale scopo, immettere l'alias e lo spazio dei nomi nel formato spazio dei *nomi alias* = . Questa operazione è utile se si usano spazi dei nomi lunghi, ad esempio `Http= MyOrg.ObjectLib.Internet.WebRequestMethods.Http`.

 **Aggiungi importazione utente**

Fare clic su questo pulsante per aggiungere lo spazio specificato nella casella **Spazi dei nomi importati** all'elenco degli spazi dei nomi importati. Il pulsante è attivo solo se lo spazio dei nomi specificato non è presente nell'elenco.

 **Elenco Spazi dei nomi**

Questo elenco visualizza tutti gli spazi dei nomi disponibili. Le caselle di controllo per gli spazi dei nomi inclusi nel progetto sono selezionate.

 **Aggiorna importazione utente**

Selezionare uno spazio dei nomi specificato dall'utente nell'elenco degli spazi dei nomi, digitare il nome come cui si vuole sostituirlo nella casella **Spazi dei nomi importati** e quindi fare clic su questo pulsante per impostare il nuovo spazio dei nomi. Il pulsante è attivo solo se lo spazio dei nomi selezionato è tra quelli aggiunti all'elenco mediante il pulsante **Aggiungi importazione utente**. È possibile aggiungere:

- Classi o spazi dei nomi, ad esempio <xref:System.Math?displayProperty=fullName>.

- Importazioni con alias, ad esempio `VB=Microsoft.VisualBasic`.

- Spazi dei nomi XML, ad esempio `<xmlns:xsl="http://www.w3.org/1999/XSL/Transform">`.

## <a name="see-also"></a>Vedi anche

- [Gestione dei riferimenti in un progetto](../../ide/managing-references-in-a-project.md)
- [Procedura: Aggiungere o rimuovere spazi dei nomi importati (Visual Basic)](../../ide/how-to-add-or-remove-imported-namespaces-visual-basic.md)
- [Istruzione Imports (spazio dei nomi XML)](/dotnet/visual-basic/language-reference/statements/imports-statement-xml-namespace)
