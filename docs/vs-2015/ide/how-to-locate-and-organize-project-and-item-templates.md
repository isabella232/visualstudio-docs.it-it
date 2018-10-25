---
title: 'Procedura: Individuare e organizzare modelli di progetto e modelli di elementi | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- project templates [Visual Studio], locations
- custom template locations [Visual Studio]
- item templates, locations
- Visual Studio templates, locations
- project templates [Visual Studio], displaying
- templates [Visual Studio], locations
ms.assetid: 71f9ed52-c9c9-4818-9bce-c279ffaa0438
caps.latest.revision: 28
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 2a3954e5d18db6585c8dbda017773969f96b33de
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49830977"
---
# <a name="how-to-locate-and-organize-project-and-item-templates"></a>Procedura: individuare e organizzare modelli di progetto e modelli di elementi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

I file di modello devono essere inseriti in un percorso riconosciuto da Visual Studio, in modo che siano visualizzati nelle finestre di dialogo **Nuovo progetto** e **Aggiungi nuovo elemento**. Per i modelli è possibile creare sottocategorie personalizzate che verranno poi visualizzate nell'interfaccia utente.  
  
## <a name="locating-templates"></a>Individuazione dei modelli  
 Per impostazione predefinita, Visual Studio cerca i modelli di progetto e i modelli di elemento in due percorsi. Se in questi percorsi esiste un file compresso che include un file con estensione vstemplate, nella finestra di dialogo **Nuovo progetto** o **Aggiungi nuovo elemento** viene visualizzato un modello.  
  
### <a name="installed-templates"></a>Modelli installati  
 Per impostazione predefinita, i modelli installati con il prodotto risiedono nei percorsi seguenti:  
  
- \\*VisualStudioInstallationDirectory*\Common7\IDE\ItemTemplates\\*Linguaggio*\\*Impostazioni locali*\  
  
- \\*VisualStudioInstallationDirectory*\Common7\IDE\ProjectTemplates\\*Linguaggio*\\*Impostazioni locali\\*  
  
  Ad esempio, la directory seguente contiene i modelli di progetto personalizzati di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] per la lingua inglese:  
  
  C:\\*VisualStudioInstallationDirectory*\Common7\IDE\ItemTemplates\VisualBasic\1033\  
  
### <a name="custom-templates"></a>Modelli personalizzati  
 Per impostazione predefinita, i modelli personalizzati risiedono nel percorso seguente:  
  
- \Documenti\Visual Studio *Versione*\Templates\ProjectTemplates\\*Linguaggio*\  
  
- \Documenti\Visual Studio *Versione*\Templates\ItemTemplates\\*Linguaggio*\  
  
  La directory seguente, ad esempio, contiene i modelli di progetto personalizzati di [!INCLUDE[csprcs](../includes/csprcs-md.md)]:  
  
  C:\Documents and settings\nomeutente\documenti\<versione documenti\\< versione di Visual Studio\>\Templates\ProjectTemplates\Visual c# \  
  
  I modelli personalizzati non includono una sottodirectory per i modelli localizzati. È possibile modificare la directory predefinita per i modelli personalizzati nella finestra di dialogo **Opzioni**, in **Ambiente/Progetti e soluzioni**.  
  
## <a name="organizing-templates"></a>Organizzazione dei modelli  
 Le categorie nelle finestre di dialogo **Nuovo progetto** e **Aggiungi nuovo elemento** riflettono le strutture delle directory esistenti nei percorsi dei modelli installati e dei modelli personalizzati. È possibile modificare le strutture di queste directory e organizzare i modelli in base alle esigenze.  
  
> [!NOTE]
>  Non è possibile creare una nuova categoria a livello di linguaggio di programmazione. Le nuove categorie possono essere create solo all'interno di ciascun linguaggio.  
  
 Se le directory dei modelli installati e personalizzati di un particolare linguaggio non presentano la stessa struttura, ovvero se, ad esempio, all'interno di una cartella sono presenti directory non presenti nell'altra, l'insieme di categorie visualizzato nella finestra di dialogo **Nuovo progetto** è costituito dall'unione di tutte le categorie.  
  
### <a name="organizing-installed-templates"></a>Organizzazione dei modelli installati  
 È possibile organizzare i modelli installati creando sottodirectory all'interno della cartella del linguaggio di programmazione. Nelle finestre di dialogo **Nuovo progetto** e **Aggiungi nuovo elemento** queste sottodirectory verranno rappresentate come cartelle virtuali all'interno di ogni linguaggio.  
  
##### <a name="to-create-new-installed-project-template-categories"></a>Per creare nuove categorie dei modelli di progetto installati  
  
1. Creare una cartella nella cartella del linguaggio della directory dei modelli installati. Ad esempio, per creare una categoria Office per i modelli di progetto di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], è necessario creare la directory seguente:  
  
    \\*DirectoryInstallazioneVisualStudio*\Common7\IDE\ProjectTemplates\VisualBasic\1033\Office\  
  
2. Inserire nella nuova cartella tutti modelli di questa categoria.  
  
3. Chiudere tutte le istanze di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
4. Nel menu **Start** fare clic su **Esegui**, digitare **cmd**, e fare clic su **OK**.  
  
5. Al prompt dei comandi, passare alla directory che contiene devenv.exe e digitare **devenv /installvstemplates**.  
  
6. Eseguire [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
7. Scegliere **Nuovo** dal menu **File**, quindi fare clic su **Progetto**.  
  
8. Verificare che la categoria Office sia visualizzata nel riquadro **Tipi di progetto** della finestra di dialogo **Nuovo progetto**, in [!INCLUDE[vbprvb](../includes/vbprvb-md.md)].  
  
   È anche possibile raggruppare in una cartella personalizzata un subset dei modelli degli elementi del progetto.  
  
##### <a name="to-create-new-installed-item-template-categories"></a>Per creare nuove categorie dei modelli di elemento installati  
  
1.  Creare una cartella nella cartella del linguaggio della directory dei modelli installati. Ad esempio, per creare una categoria Web per i modelli di elemento di [!INCLUDE[csprcs](../includes/csprcs-md.md)], è necessario creare la directory seguente:  
  
     \\*DirectoryInstallazioneVisualStudio*\Common7\IDE\ItemTemplates\CSharp\1033\Web\  
  
2.  Inserire nella nuova cartella tutti modelli di questa categoria.  
  
3.  Chiudere tutte le istanze di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
4.  Nel menu **Start** fare clic su **Esegui**, digitare **cmd**, e fare clic su **OK**.  
  
5.  Al prompt dei comandi, passare alla directory che contiene devenv.exe e digitare **devenv /setup**.  
  
6.  Eseguire [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
7.  Creare un progetto oppure aprire un progetto esistente.  
  
8.  Nel menu **Progetto** fare clic su **Aggiungi nuovo elemento**.  
  
9. Verificare che la categoria Web sia visualizzata nel riquadro **Tipi di progetto** della finestra di dialogo **Aggiungi nuovo elemento**.  
  
### <a name="organizing-custom-templates"></a>Organizzazione dei modelli personalizzati  
 È possibile organizzare i modelli personalizzati in categorie proprie aggiungendo nuove cartelle nel percorso dei modelli personalizzati, La finestra di dialogo **Nuovo progetto** riflette tutte le modifiche apportate alle categorie dei modelli.  
  
##### <a name="to-create-new-custom-project-template-categories"></a>Per creare nuove categorie dei modelli di progetto personalizzati  
  
1. Creare una cartella nella cartella del linguaggio della directory dei modelli di progetto personalizzati. Ad esempio, per creare una categoria HelloWorld per i modelli di [!INCLUDE[csprcs](../includes/csprcs-md.md)], è necessario creare la directory seguente:  
  
    Documenti \My\\< versione di Visual Studio\>\Templates\ProjectTemplates\CSharp\HelloWorld\  
  
2. Inserire nella nuova cartella tutti modelli di questa categoria.  
  
3. Scegliere **Nuovo** dal menu **File**, quindi fare clic su **Progetto**.  
  
4. Verificare che la categoria HelloWorld sia visualizzata nel riquadro **Tipi di progetto** della finestra di dialogo **Nuovo progetto**, in [!INCLUDE[csprcs](../includes/csprcs-md.md)].  
  
   È anche possibile raggruppare in una cartella personalizzata un subset dei modelli di elemento personalizzati.  
  
##### <a name="to-create-new-custom-item-template-categories"></a>Per creare nuove categorie di modelli di elemento personalizzati  
  
1.  Creare una cartella nella cartella del linguaggio della directory dei modelli di elemento personalizzati. Ad esempio, per creare una categoria HelloWorld per i modelli di [!INCLUDE[csprcs](../includes/csprcs-md.md)], è necessario creare la directory seguente:  
  
     Documenti \My\\< versione di Visual Studio\>\Templates\ItemTemplates\CSharp\HelloWorld\  
  
2.  Inserire nella nuova cartella tutti modelli di questa categoria.  
  
3.  Creare un progetto oppure aprire un progetto esistente.  
  
4.  Nel menu **Progetto** fare clic su **Aggiungi nuovo elemento**.  
  
5.  Verificare che la categoria HelloWorld sia visualizzata nel riquadro **Tipi di progetto** della finestra di dialogo **Aggiungi nuovo elemento**.  
  
### <a name="displaying-templates-in-parent-categories"></a>Visualizzazione dei modelli in categorie padre  
 I modelli inclusi nelle sottocategorie possono essere visualizzati nelle relative categorie padre tramite l'elemento `NumberOfParentCategoriesToRollUp` incluso nel file con estensione vstemplate. Questa procedura è identica sia per i modelli di progetto sia per i modelli di elemento.  
  
##### <a name="to-display-templates-in-parent-categories"></a>Per visualizzare i modelli in categorie padre  
  
1.  Individuare il file ZIP che contiene il modello.  
  
2.  Estrarre il file ZIP.  
  
3.  Aprire il file vstemplate nel [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
4.  Nell'elemento `TemplateData` aggiungere un elemento `NumberOfParentCategoriesToRollUp`. Ad esempio, il codice riportato di seguito rende visibile il modello nella categoria padre, ma non ai livelli superiori.  
  
    ```  
    <TemplateData>  
        ...  
        <NumberOfParentCategoriesToRollUp>  
            1  
        </NumberOfParentCategoriesToRollUp>  
        ...  
    </TemplateData>  
    ```  
  
5.  Salvare e chiudere il file vstemplate.  
  
6.  Selezionare i file inclusi nel modello, fare clic con il pulsante destro del mouse sulla selezione, scegliere **Invia a** e quindi fare clic su **Cartella compressa**. I file verranno compressi in un file ZIP.  
  
7.  Eliminare i file di modello estratti e il vecchio file di modello ZIP.  
  
8.  Inserire il nuovo file ZIP nella stessa directory del file ZIP eliminato.  
  
## <a name="see-also"></a>Vedere anche  
 [Personalizzazione di modelli](../ide/customizing-project-and-item-templates.md)   
 [Riferimenti allo schema dei modelli di Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [NumberOfParentCategoriesToRollUp (modelli di Visual Studio)](../extensibility/numberofparentcategoriestorollup-visual-studio-templates.md)   
 [Procedura: Creare modelli di progetto](../ide/how-to-create-project-templates.md)   
 [Procedura: Creare modelli di elementi](../ide/how-to-create-item-templates.md)



