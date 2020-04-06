---
title: Creazione di gruppi riutilizzabili di pulsanti Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- button groups, creating in VSPackages
- VSPackages, creating reusable button groups
- buttons, creating reusable groups
ms.assetid: 0c561617-fb86-476d-8bd1-c6e5e7464c65
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ddfba6701890f73ce6438ddc03a338912841a37d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739468"
---
# <a name="create-reusable-groups-of-buttons"></a>Creare gruppi riutilizzabili di pulsanti
Un gruppo di comandi è una raccolta di comandi che vengono sempre visualizzati insieme in un menu o una barra degli strumenti. Qualsiasi gruppo di comandi può essere riutilizzato assegnandolo a menu padre diversi nella sezione CommandPlacements del file *vsct.*

 I gruppi di comandi contengono in genere pulsanti, ma possono anche contenere altri menu o caselle combinate.

## <a name="to-create-a-reusable-group-of-buttons"></a>Per creare un gruppo riutilizzabile di pulsanti

1. Creare un progetto `ReusableButtons`VSIX denominato . Per ulteriori informazioni, consultate [Creare un'estensione con un comando](../extensibility/creating-an-extension-with-a-menu-command.md)di menu.

2. Quando si apre il progetto, aggiungere un modello di elemento di comando personalizzato denominato **ReusableCommand**. In **Esplora soluzioni**fare clic con il pulsante destro del mouse sul nodo del progetto e **scegliere Aggiungi** > **nuovo elemento**. Nella finestra di dialogo **Aggiungi nuovo elemento** passare a**Estensibilità** **di Visual C,** > quindi selezionare **Comando personalizzato**. Nel campo **Nome** nella parte inferiore della finestra modificare il nome del file di comando in *ReusableCommand.cs*.

3. Nel file *vsct* passare alla sezione Symbols e individuare l'elemento GuidSymbol che contiene gruppi e comandi per il progetto. Deve essere denominato guidReusableCommandPackageCmdSet.

4. Aggiungere un IDSymbol per ogni pulsante che verrà aggiunto al gruppo, come nell'esempio seguente.

    ```xml
    <GuidSymbol name="guidReusableCommandPackageCmdSet" value="{7f383b2a-c6b9-4c1d-b4b8-a26dc5b60ca1}">
        <IDSymbol name="MyMenuGroup" value="0x1020" />
        <IDSymbol name="ReusableCommandId" value="0x0100" />
        <IDSymbol name="SecondReusableCommandId" value="0x0200" />
    </GuidSymbol>
    ```

     Per impostazione predefinita, il modello di elemento di comando crea un gruppo denominato **MyMenuGroup** e un pulsante con il nome fornito, insieme a una voce IDSymbol per ognuno.

5. Nella sezione Gruppi creare un elemento Group con gli stessi attributi GUID e ID specificati nella sezione Symbols. È inoltre possibile utilizzare un gruppo esistente o utilizzare la voce fornita dal modello di comando, come nell'esempio seguente. Questo gruppo viene visualizzato nel menu **Strumenti**

    ```xml
    <Groups>
        <Group guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" priority="0x0600">
              <Parent guid="guidSHLMainMenu" id="IDM_VS_MENU_TOOLS"/>
        </Group>
    </Groups>
    ```

## <a name="to-create-a-group-of-buttons-for-reuse"></a>Per creare un gruppo di pulsanti da riutilizzare

1. È possibile inserire un comando o un menu in un gruppo utilizzando il gruppo come elemento padre nella definizione del comando o del menu oppure inserendo il comando o il menu nel gruppo utilizzando la sezione CommandPlacements.

     Nella sezione Pulsanti definire un pulsante con il gruppo come padre oppure usare il pulsante fornito dal modello di pacchetto, come illustrato nell'esempio seguente.

    ```xml
    <Button guid="guidReusableCommandPackageCmdSet" id="ReusableCommandId" priority="0x0100" type="Button">
        <Parent guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" />
        <Icon guid="guidImages" id="bmpPic1" />
        <Strings>
            <ButtonText>Invoke ReusableCommand</ButtonText>
        </Strings>
    </Button>
    ```

2. Se un pulsante deve essere visualizzato in più gruppi, creare una voce per esso nella sezione CommandPlacements, che deve essere inserita dopo il Commands sezione. Impostare gli attributi GUID e ID dell'elemento CommandPlacement in modo che corrispondano a quelli del pulsante che si desidera posizionare, quindi impostare il GUID e l'ID del relativo elemento Parent su quelli del gruppo di destinazione, come illustrato nell'esempio seguente.

    ```xml
    <CommandPlacements>
        <CommandPlacement guid="guidReusableCommandPackageCmdSet" id="SecondReusableCommandId" priority="0x105">
          <Parent guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" />
        </CommandPlacement>
    </CommandPlacements>
    ```

    > [!NOTE]
    > Il valore del campo Priorità determina la posizione del comando nel nuovo gruppo di comandi. Le priorità impostate nell'elemento CommandPlacement sostituiscono quelle impostate nella definizione dell'elemento. I comandi con valori di priorità più bassi vengono visualizzati prima dei comandi con valori di priorità più elevati. Sono consentiti valori di priorità duplicati, ma la posizione relativa dei comandi con lo stesso valore di priorità non può essere garantita perché l'ordine in cui il comando **devenv /setup** crea l'interfaccia finale dal Registro di sistema potrebbe non essere coerente.

## <a name="to-put-a-reusable-group-of-buttons-on-a-menu"></a>Per inserire un gruppo riutilizzabile di pulsanti in un menu

1. Creare una voce `CommandPlacements` nella sezione. Impostare il GUID `CommandPlacement` e l'ID dell'elemento su quelli del gruppo e impostare il GUID e l'ID padre su quelli del percorso di destinazione.

    La sezione CommandPlacements deve essere posizionata subito dopo la sezione Commands:

   ```xml
   <CommandTable>
   ...
     <Commands>... </Commands>
     <CommandPlacements>... </CommandPlacements>
   ...
   </CommandTable>
   ```

    Un gruppo di comandi può essere incluso in più di un menu. Il menu padre può essere uno creato dall'utente, uno fornito da [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] (come descritto in *ShellCmdDef.vsct* o *SharedCmdDef.vsct*) o uno definito in un altro VSPackage. Il numero di livelli padre è illimitato fino a [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] quando il menu padre viene connesso o a un menu di scelta rapida che viene visualizzato da un VSPackage.The number of parenting layers is unlimited as long as the parent menu is eventually connected to or to a shortcut menu that is displayed by a VSPackage.

    Nell'esempio seguente il gruppo viene inserito nella barra degli strumenti di **Esplora soluzioni,** a destra degli altri pulsanti.

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
