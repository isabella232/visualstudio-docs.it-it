---
title: Creazione di gruppi riutilizzabili di pulsanti | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- button groups, creating in VSPackages
- VSPackages, creating reusable button groups
- buttons, creating reusable groups
ms.assetid: 0c561617-fb86-476d-8bd1-c6e5e7464c65
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 454e42ba0b99d47048fa54527e8771f8294dcbc9
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66351984"
---
# <a name="create-reusable-groups-of-buttons"></a>Creazione di gruppi riutilizzabili di pulsanti
Un gruppo di comandi è una raccolta di comandi che vengono sempre visualizzati insieme in un menu o sulla barra degli strumenti. Qualsiasi gruppo di comandi può essere riusato assegnandolo ai menu padre diverso nella sezione CommandPlacements del *vsct* file.

 Gruppi di comandi in genere contengono pulsanti, ma possono anche contenere altre caselle combinate o menu.

## <a name="to-create-a-reusable-group-of-buttons"></a>Per creare un gruppo riutilizzabile di pulsanti

1. Creare un progetto VSIX denominato `ReusableButtons`. Per altre informazioni, vedere [creare un'estensione con un comando di menu](../extensibility/creating-an-extension-with-a-menu-command.md).

2. Quando si apre il progetto, aggiungere un modello di elemento di comando personalizzato denominato **ReusableCommand**. Nel **Esplora soluzioni**, fare doppio clic sul nodo del progetto e selezionare **Add** > **nuovo elemento**. Nel **Aggiungi nuovo elemento** finestra di dialogo passa alla **Visual c#**  > **Extensibility** e selezionare **comando personalizzato**. Nel **Name** campo nella parte inferiore della finestra, modificare il nome di file di comando da *ReusableCommand.cs*.

3. Nel *vsct* file, vedere la sezione di simboli e trovare l'elemento GuidSymbol che contiene gruppi e i comandi per il progetto. Devono essere denominato guidReusableCommandPackageCmdSet.

4. Aggiungere un IDSymbol per ciascun pulsante che verrà aggiunta al gruppo, come nell'esempio seguente.

    ```xml
    <GuidSymbol name="guidReusableCommandPackageCmdSet" value="{7f383b2a-c6b9-4c1d-b4b8-a26dc5b60ca1}">
        <IDSymbol name="MyMenuGroup" value="0x1020" />
        <IDSymbol name="ReusableCommandId" value="0x0100" />
        <IDSymbol name="SecondReusableCommandId" value="0x0200" />
    </GuidSymbol>
    ```

     Per impostazione predefinita, il modello di elemento di comando crea un gruppo denominato **MyMenuGroup** e un pulsante con il nome specificato, insieme a una voce IDSymbol per ognuno.

5. Nella sezione Groups, creare un elemento di gruppo che ha gli stessi attributi GUID e ID di quelle contenute nella sezione dei simboli. È anche possibile usare un gruppo esistente o usare la voce che viene fornita dal modello di comando, come nell'esempio seguente. Questo gruppo sono presenti il **strumenti** menu

    ```xml
    <Groups>
        <Group guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" priority="0x0600">
              <Parent guid="guidSHLMainMenu" id="IDM_VS_MENU_TOOLS"/>
        </Group>
    </Groups>
    ```

## <a name="to-create-a-group-of-buttons-for-reuse"></a>Per creare un gruppo di pulsanti per il riutilizzo

1. È possibile inserire un comando o un menu in un gruppo usando il gruppo come elemento padre nella definizione di comando o menu, oppure inserendo il comando o il menu del gruppo usando la sezione CommandPlacements.

     Nella sezione pulsanti definiscono un pulsante con il gruppo come elemento padre, o usare il pulsante che viene fornito dal modello di pacchetto, come illustrato nell'esempio seguente.

    ```xml
    <Button guid="guidReusableCommandPackageCmdSet" id="ReusableCommandId" priority="0x0100" type="Button">
        <Parent guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" />
        <Icon guid="guidImages" id="bmpPic1" />
        <Strings>
            <ButtonText>Invoke ReusableCommand</ButtonText>
        </Strings>
    </Button>
    ```

2. Se un pulsante deve apparire in più di un gruppo, creare una voce per tale nella sezione CommandPlacements, che deve essere inserita dopo la sezione di comandi. Impostare gli attributi GUID e ID dell'elemento CommandPlacement affinché corrispondano a quelle del pulsante che si desidera posizionare e quindi impostare il GUID e ID dell'elemento padre a quelle del gruppo di destinazione, come illustrato nell'esempio seguente.

    ```xml
    <CommandPlacements>
        <CommandPlacement guid="guidReusableCommandPackageCmdSet" id="SecondReusableCommandId" priority="0x105">
          <Parent guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" />
        </CommandPlacement>
    </CommandPlacements>
    ```

    > [!NOTE]
    > Il valore del campo priorità determina la posizione del comando nel nuovo gruppo di comando. Le priorità di impostare il CommandPlacement elemento sostituiscono quelli impostati nella definizione di elemento. I comandi che hanno valori di priorità inferiore vengono visualizzati prima i comandi che hanno valori di priorità superiore. Sono consentiti valori di priorità identici, ma la posizione relativa dei comandi con lo stesso valore di priorità non può essere garantita poiché l'ordine in cui il **devenv /setup** comando crea l'interfaccia finale dal Registro di sistema potrebbe non essere coerente.

## <a name="to-put-a-reusable-group-of-buttons-on-a-menu"></a>Inserire un gruppo riutilizzabile di pulsanti in un menu

1. Creare una voce nel `CommandPlacements` sezione. Impostare il GUID e ID del `CommandPlacement` elemento a quelli del gruppo e impostare l'elemento padre GUID e ID a quelle del percorso di destinazione.

    La sezione CommandPlacements deve essere posizionata immediatamente dopo la sezione di comandi:

   ```xml
   <CommandTable>
   ...
     <Commands>... </Commands>
     <CommandPlacements>... </CommandPlacements>
   ...
   </CommandTable>
   ```

    Un gruppo di comandi può essere inclusi in più di un menu. Menu del padre può essere uno che è stato creato, che viene fornito da [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] (come descritto in *ShellCmdDef.vsct* oppure *SharedCmdDef.vsct*), o che viene definito in un altro VSPackage. Il numero di livelli padre è illimitato, purché il menu padre alla fine è connesso a [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] o a un menu di scelta rapida che viene visualizzato da un pacchetto VSPackage.

    Nell'esempio seguente inserisce il gruppo di nel **Esplora soluzioni** sulla barra degli strumenti, a destra degli altri pulsanti.

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
