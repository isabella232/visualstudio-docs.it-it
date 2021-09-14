---
title: 'Procedura: Contrassegnare i controlli come Cassaforte controlli | Microsoft Docs'
description: Contrassegnare i controlli come controlli sicuri nella proprietà Cassaforte Control Entries di un SharePoint di progetto o in Progettazione pacchetti quando si aggiunge un assembly.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, safe controls
- SharePoint development in Visual Studio, advanced packaging tools
- safe controls [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: e96a27be0ae8a71125964e27da99270d9142886c
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126711438"
---
# <a name="how-to-mark-controls-as-safe-controls"></a>Procedura: Contrassegnare i controlli come controlli sicuri
  Per motivi di sicurezza, SharePoint tra i controlli Web protetti dall'inserimento di script e i controlli Web che non lo sono. I controlli protetti, *o controlli* sicuri, possono essere accessibili da utenti non attendibili. È possibile contrassegnare i controlli come sicuri nella proprietà Cassaforte Control Entries  di un elemento di progetto SharePoint o in Progettazione pacchetti quando si aggiunge un assembly al pacchetto. Per ulteriori informazioni, vedere

- [web.config file Impostazioni e](/previous-versions/office/developer/sharepoint-2007/bb802890(v=office.12)) registrazione [di](/previous-versions/office/developer/sharepoint2003/dd587360(v=office.11))un assembly web part come Cassaforte controllo .

> [!IMPORTANT]
> Queste procedure sono a scopo illustrativo. Contrassegnare i controlli come sicuri solo se si è certi che siano sicuri.

## <a name="marking-safe-controls-in-the-safe-control-entries-property"></a>Contrassegno Cassaforte controlli nella Cassaforte delle voci di controllo

#### <a name="to-mark-controls-as-safe-or-unsafe-in-the-safe-control-entries-property"></a>Per contrassegnare i controlli come sicuri o non sicuri nella proprietà delle voci di controllo sicuro

1. Creare una SharePoint con un progetto web part visuale.

2. Aggiungere due controlli alla web part: una casella di testo e un pulsante. Lasciare i nomi ai valori predefiniti, TextBox1 e Button1, rispettivamente.

3. Aggiungere due voci alla proprietà Web part Cassaforte **Control Entries.** A tale scopo, scegliere il pulsante con i puntini di sospensione ( ASP.NET ![Mobile Designer](../sharepoint/media/mwellipsis.gif "Ellisse di ASP.NET Mobile Designer")) accanto alla proprietà Cassaforte **Control Entries** nella **finestra** Proprietà.

     Verrà **Cassaforte finestra di dialogo Voci di** controllo.

4. Nella finestra **Cassaforte voci** di controllo scegliere  due volte il pulsante Aggiungi per  aggiungere due voci di controllo sicuro al riquadro Membri: una per il pulsante e una per la casella di testo.

5. Scegliere la prima voce di controllo sicuro e quindi impostare il valore della proprietà **Cassaforte su** **False**, la proprietà **Type Name** su **Button1** e la proprietà **Cassaforte Against Script** su **False**.

     Questo passaggio identifica il controllo pulsante come controllo non sicuro.

6. Scegliere la seconda voce di controllo sicura nell'elenco. Lasciare il valore della proprietà **Cassaforte** impostata su **True** e impostarne la proprietà **Type Name** su **TextBox1** e la relativa proprietà Cassaforte **Against Script** su **True**.

     Il controllo casella di testo è ora contrassegnato come controllo sicuro dall'inserimento di script.

7. Scegliere il pulsante **OK** per chiudere la finestra di dialogo.

## <a name="marking-safe-controls-in-the-package-designer"></a>Contrassegno Cassaforte controlli in Progettazione pacchetti

#### <a name="to-mark-controls-as-safe-or-unsafe-in-the-package-designer"></a>Per contrassegnare i controlli come sicuri o non sicuri in Progettazione pacchetti

1. Creare una SharePoint con un progetto web part visuale.

2. Aggiungere due controlli alla web part: una casella di testo e un pulsante. Lasciare i nomi ai valori predefiniti, TextBox1 e Button1, rispettivamente.

     Prendere nota dello spazio dei nomi del controllo perché viene usato in un secondo momento.

3. Nella barra dei menu scegliere **Compila**  >  **soluzione per** compilare il progetto.

4. Creare un'SharePoint soluzione.

5. In **Esplora soluzioni** aprire il menu di scelta rapida per il file *Package.Package* e quindi scegliere Apri **per** aprire **Progettazione pacchetti**.

6. In **Progettazione pacchetti** scegliere la **scheda** Avanzate.

7. In **Assembly aggiuntivi** scegliere il pulsante **Aggiungi** e quindi Aggiungi **assembly esistente** dall'elenco.

8. Nella finestra **di dialogo Aggiungi assembly** esistente scegliere i puntini di sospensione ( ASP.NET Mobile ![Designer](../sharepoint/media/mwellipsis.gif "Ellisse di ASP.NET Mobile Designer")) accanto a **Percorso origine**.

9. Scegliere l'assembly SharePoint soluzione creata nel passaggio 1 e quindi scegliere il **pulsante** Apri.

10. Per questo esempio, lasciare **l'opzione Destinazione** distribuzione come GlobalAssemblyCache.

     Questo passaggio determina la distribuzione dell'assembly nella Global Assembly Cache (GAC) del sistema. Se si vuole distribuire l'assembly nella cartella dell'applicazione Web (Bin), selezionare questa opzione. Per altre informazioni, vedere [Distribuzione di Web part in SharePoint Foundation.](/previous-versions/office/developer/sharepoint-2010/cc768621(v=office.14))

11. Nella casella **Cassaforte controlli** selezionare il pulsante Fare clic qui per aggiungere un **nuovo elemento.**

12. Immettere i valori per le proprietà della tabella seguente.

    |Nome della proprietà|Valore|
    |-------------------|-----------|
    |Spazio dei nomi|Spazio dei nomi completo per il controllo, ad esempio **BdcModelProject1.VisualWebPart1.**|
    |Nome tipo|Button1|
    |Nome assembly|Nome sicuro dell'assembly, ad esempio: Microsoft. Office. SharePoint. ClientExtensions, Version=14.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c.|
    |Safe|Deselezionare **la Cassaforte** di controllo.|
    |Cassaforte Contro script|Lasciare **deselezionata Cassaforte la casella di controllo Contro** script.|

    > [!NOTE]
    > Il **valore Nome** assembly per  gli assembly aggiunti tramite la scheda Avanzate di **Progettazione** pacchetti non può essere un token, ma deve essere un assembly con nome sicuro. Per altre informazioni, vedere [Creazione e utilizzo degli assembly con nome sicuro](/previous-versions/dotnet/netframework-4.0/xwb8f617(v=vs.100)).

13. Premere TAB **per** creare un'altra voce di controllo sicuro.

14. Scegliere di **nuovo il pulsante Fare clic** qui per aggiungere un nuovo elemento.

15. Immettere i valori per le proprietà della tabella seguente.

    |Nome della proprietà|Valore|
    |-------------------|-----------|
    |Spazio dei nomi|Spazio dei nomi completo per il controllo, ad esempio **BdcModelProject1.VisualWebPart1.**|
    |Nome tipo|TextBox1|
    |Nome assembly|Nome sicuro dell'assembly, ad esempio: Microsoft. Office. SharePoint. ClientExtensions, Version=14.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c.|
    |Safe|Selezionare la **Cassaforte** di controllo.|
    |Cassaforte Contro script|Selezionare la **casella Cassaforte da script.**|

16. Premere **TAB** e quindi fare clic sul **pulsante OK** per chiudere la finestra di dialogo.

## <a name="see-also"></a>Vedi anche
- [Fornire informazioni sulla creazione di pacchetti e sulla distribuzione negli elementi del progetto](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)
- [Creare pacchetti e distribuire SharePoint soluzioni](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
