---
title: Creazione di gruppi riutilizzabili di pulsanti | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- button groups, creating in VSPackages
- VSPackages, creating reusable button groups
- buttons, creating reusable groups
ms.assetid: 0c561617-fb86-476d-8bd1-c6e5e7464c65
caps.latest.revision: 45
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6ac1fd0dc242ae8b8979a3f420f5e1c4d837f62b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839920"
---
# <a name="creating-reusable-groups-of-buttons"></a>Creazione di gruppi riutilizzabili di pulsanti
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Un gruppo di comandi è una raccolta di comandi che vengono sempre visualizzati insieme in un menu o in una barra degli strumenti. Qualsiasi gruppo di comandi può essere riutilizzato assegnando il gruppo a diversi menu padre nella sezione CommandPlacements del file. vsct.  
  
 I gruppi di comandi contengono in genere pulsanti, ma possono contenere anche altri menu o caselle combinate.  
  
### <a name="to-create-a-reusable-group-of-buttons"></a>Per creare un gruppo di pulsanti riutilizzabile  
  
1. Creare un progetto VSIX denominato `ReusableButtons` . Per ulteriori informazioni, vedere [creazione di un'estensione con un comando di menu](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
2. Quando si apre il progetto, aggiungere un modello di elemento di comando personalizzato denominato **ReusableCommand**. Nella **Esplora soluzioni**fare clic con il pulsante destro del mouse sul nodo del progetto e scegliere **Aggiungi/nuovo elemento**. Nella finestra di dialogo **Aggiungi nuovo elemento** passare a **Visual C#/extensibility** e selezionare **comando personalizzato**. Nel campo **nome** nella parte inferiore della finestra modificare il nome del file di comando in **ReusableCommand.cs**.  
  
3. Nel file con estensione vsct passare alla sezione simboli e trovare l'elemento GuidSymbol che contiene i gruppi e i comandi per il progetto. Deve essere denominata guidReusableCommandPackageCmdSet.  
  
4. Aggiungere un IDSymbol per ogni pulsante che si aggiungerà al gruppo, come nell'esempio seguente.  
  
    ```xml  
    <GuidSymbol name="guidReusableCommandPackageCmdSet" value="{7f383b2a-c6b9-4c1d-b4b8-a26dc5b60ca1}">  
        <IDSymbol name="MyMenuGroup" value="0x1020" />  
        <IDSymbol name="ReusableCommandId" value="0x0100" />  
        <IDSymbol name="SecondReusableCommandId" value="0x0200" />  
    </GuidSymbol>  
    ```  
  
     Per impostazione predefinita, il modello di elemento di comando crea un **gruppo denominato il gruppo e** un pulsante con il nome specificato, insieme a una voce IDSymbol per ciascuna.  
  
5. Nella sezione groups creare un elemento Group con gli stessi attributi GUID e ID di quelli specificati nella sezione simboli. È anche possibile usare un gruppo esistente o usare la voce fornita dal modello di comando, come nell'esempio seguente. Questo gruppo viene visualizzato nel menu **strumenti** .  
  
    ```xml  
    <Groups>  
        <Group guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" priority="0x0600">  
              <Parent guid="guidSHLMainMenu" id="IDM_VS_MENU_TOOLS"/>  
        </Group>  
    </Groups>  
    ```  
  
### <a name="to-create-a-group-of-buttons-for-reuse"></a>Per creare un gruppo di pulsanti da riutilizzare  
  
1. È possibile inserire un comando o un menu in un gruppo usando il gruppo come elemento padre nella definizione del comando o del menu oppure inserendo il comando o il menu nel gruppo usando la sezione CommandPlacements.  
  
     Nella sezione pulsanti definire un pulsante con il gruppo come padre oppure usare il pulsante fornito dal modello di pacchetto, come illustrato nell'esempio seguente.  
  
    ```xml  
    <Button guid="guidReusableCommandPackageCmdSet" id="ReusableCommandId" priority="0x0100" type="Button">  
        <Parent guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" />  
        <Icon guid="guidImages" id="bmpPic1" />  
        <Strings>  
            <ButtonText>Invoke ReusableCommand</ButtonText>  
        </Strings>  
    </Button>  
    ```  
  
2. Se un pulsante deve essere visualizzato in più di un gruppo, crearne una voce nella sezione CommandPlacements, che deve essere posizionata dopo la sezione commands. Impostare gli attributi GUID e ID dell'elemento CommandPlacement in modo che corrispondano a quelli del pulsante che si desidera posizionare, quindi impostare il GUID e l'ID del relativo elemento padre su quelli del gruppo di destinazione, come illustrato nell'esempio seguente.  
  
    ```xml  
    <CommandPlacements>  
        <CommandPlacement guid="guidReusableCommandPackageCmdSet" id="SecondReusableCommandId" priority="0x105">  
          <Parent guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" />  
        </CommandPlacement>  
    </CommandPlacements>  
    ```  
  
    > [!NOTE]
    > Il valore del campo Priority determina la posizione del comando nel nuovo gruppo di comandi. Le priorità impostate nell'elemento CommandPlacement eseguono l'override di quelle impostate nella definizione dell'elemento. I comandi con valori di priorità inferiore vengono visualizzati prima dei comandi con valori di priorità più elevati. Sono consentiti valori di priorità duplicati, ma non è possibile garantire la posizione relativa dei comandi con lo stesso valore di priorità perché l'ordine in cui il comando **devenv/setup** crea l'interfaccia finale dal registro di sistema potrebbe non essere coerente.  
  
### <a name="to-put-a-reusable-group-of-buttons-on-a-menu"></a>Per inserire un gruppo di pulsanti riutilizzabile in un menu  
  
1. Creare una voce nella `CommandPlacements` sezione. Impostare il GUID e l'ID dell' `CommandPlacement` elemento su quelli del gruppo e impostare il GUID padre e l'ID su quelli del percorso di destinazione.  
  
     La sezione CommandPlacements deve essere posizionata subito dopo la sezione commands:  
  
    ```xml  
    <CommandTable>  
    ...  
      <Commands>... </Commands>  
      <CommandPlacements>... </CommandPlacements>  
    ...   
    </CommandTable>  
    ```  
  
     Un gruppo di comandi può essere incluso in più di un menu. Il menu padre può essere uno creato, uno fornito da [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] (come descritto in ShellCmdDef. vsct o SharedCmdDef. vsct) o uno definito in un altro pacchetto VSPackage. Il numero di livelli padre è illimitato finché il menu padre viene connesso a [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] o a un menu di scelta rapida visualizzato da un pacchetto VSPackage.  
  
     Nell'esempio seguente il gruppo viene inserito sulla barra degli strumenti **Esplora soluzioni** a destra degli altri pulsanti.  
  
    ```xml  
    <CommandPlacements>  
        <CommandPlacement guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" priority="0xF00">  
          <Parent guid="guidSHLMainMenu" id="IDM_VS_TOOL_PROJWIN"/>  
        </CommandPlacement>  
    </CommandPlacements>  
    ```  
  
    ```xml  
    <CommandPlacements>  
      <CommandPlacement guid="guidButtonGroupCmdSet" id="MyMenuGroup"   
          priority="0x605">  
        <Parent guid="guidSHLMainMenu" id="IDM_VS_MENU_TOOLS" />  
      </CommandPlacement>  
    </CommandPlacements>  
  
    ```
