---
title: Localizzazione dei comandi di menu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- localize
- localization
- vsct
- menu commands
- localize visual studio
- localize vsct
ms.assetid: b04ee0f6-82ea-47e6-853a-72382267d6da
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c879072b55729e249b1aecd665d6f470f4138a75
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "65686128"
---
# <a name="localizing-menu-commands"></a>Localizzazione dei comandi di menu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile fornire il testo localizzato per i comandi di menu e barre degli strumenti creando file con estensione vsct localizzati e file con estensione resx localizzati per il pacchetto VSPackage, quindi aggiornando i file di progetto per incorporare le modifiche.  
  
 Per informazioni su come localizzare l'esperienza di installazione, vedere [localizzazione dei pacchetti VSIX](../extensibility/localizing-vsix-packages.md).  
  
## <a name="localizing-command-names"></a>Localizzazione dei nomi dei comandi  
 Nei pacchetti VSPackage, i comandi di menu e i pulsanti della barra degli strumenti sono definiti nel file con estensione vsct.  
  
1. In **Esplora soluzioni**modificare il nome del file con estensione vsct da *filename*. vsct a *filename*. en-US. vsct.  
  
2. Creare una copia di *filename*. en-US. vsct per ogni lingua localizzata.  
  
    Assegnare un nome a ogni nome *file*di copia. *Locale*. vsct, dove *impostazioni locali* è un nome di impostazioni cultura specifico. Per un elenco di valori dei nomi delle impostazioni cultura, vedere [ID delle impostazioni locali assegnati da Microsoft](https://msdn.microsoft.com/library/windows/apps/jj657969.aspx).  
  
    *Nome file*. I file *locale*. vsct conterranno il testo del menu localizzato per il pacchetto.  
  
3. Aprire ogni *nome file*. File *locale*. vsct per localizzare il testo.  
  
   1. Modificare i valori dell'elemento [ButtonText](../extensibility/buttontext-element.md) nel modo appropriato per la lingua specifica.  
  
   2. Se si forniranno icone localizzate, modificare i valori [bitmap](../extensibility/bitmap-element.md) in modo che puntino ai file di destinazione.  
  
      Nell'esempio seguente viene illustrato il testo del pulsante inglese e spagnolo per un comando per aprire una finestra degli strumenti di Esplora albero.  
  
      [FamilyTree. en-US. vsct]  
  
   ```xml  
   <Button guid="guidLocalizedPackageCmdSet" id="cmdidFamilyTree" priority="0x0100" type="Button">  
     <Parent guid="guidSHLMainMenu" id="IDG_VS_WNDO_OTRWNDWS1"/>  
     <Icon guid="guidImages" id="bmpPic2" />  
     <Strings>  
       <CommandName>cmdidFamilyTree</CommandName>  
       <ButtonText>Family Tree Explorer</ButtonText>  
     </Strings>  
   </Button>  
   ```  
  
    [FamilyTree.es-ES. vsct]  
  
   ```xml  
   <Button guid="guidLocalizedPackageCmdSet" id="cmdidFamilyTree" priority="0x0100" type="Button">  
     <Parent guid="guidSHLMainMenu" id="IDG_VS_WNDO_OTRWNDWS1"/>  
     <Icon guid="guidImages" id="bmpPic2" />  
     <Strings>  
       <CommandName>cmdidFamilyTree</CommandName>  
       <ButtonText>Explorar el arbol genealogico</ButtonText>  
     </Strings>  
   </Button>  
  
   ```  
  
## <a name="localizing-other-text-resources"></a>Localizzazione di altre risorse di testo  
 Le risorse di testo diverse dai nomi dei comandi sono definite nei file di risorse (con estensione resx).  
  
1. Rinominare VSPackage. resx in VSPackage. en-US. resx.  
  
2. Creare una copia del file VSPackage. en-US. resx per ogni lingua localizzata.  
  
     Assegnare un nome a ogni copia VSPackage. *Locale*. resx, dove *impostazioni locali* è un nome di impostazioni cultura specifico.  
  
3. Rinominare resources. resx in resources. en-US. resx.  
  
4. Creare una copia del file resources. en-US. resx per ogni lingua localizzata.  
  
     Assegnare un nome a ogni risorsa di copia. *Locale*. resx, dove *impostazioni locali* è un nome di impostazioni cultura specifico.  
  
5. Aprire ogni file. resx per modificare i valori stringa in base alla lingua e alle impostazioni cultura specifiche. Nell'esempio seguente viene illustrata la definizione di risorsa localizzata per la barra del titolo di una finestra degli strumenti.  
  
     [Resources. en-US. resx]  
  
    ```xml  
    <data name="ToolWindowTitle" xml:space="preserve">  
      <value>Family Tree Explorer</value>  
    </data>  
    ```  
  
     [Resources.es-ES. resx]  
  
    ```xml  
    <data name="ToolWindowTitle" xml:space="preserve">  
      <value>Explorador del arbol genealogico</value>  
    </data>  
  
    ```  
  
## <a name="incorporating-localized-resources-into-the-project"></a>Incorporamento di risorse localizzate nel progetto  
 Per incorporare le risorse localizzate, è necessario modificare il file assemblyinfo.cs e il file di progetto.  
  
1. Dal nodo **Proprietà** in **Esplora soluzioni**aprire AssemblyInfo.cs o AssemblyInfo. vb nell'editor.  
  
2. Aggiungere la voce seguente.  
  
    ```csharp  
    [assembly: NeutralResourcesLanguage("en-US", UltimateResourceFallbackLocation.Satellite)]  
    ```  
  
     In questo modo viene impostata la lingua predefinita per l'inglese (Stati Uniti).  
  
3. Scaricare il progetto.  
  
4. Aprire il file di progetto nell'editor.  
  
5. Individuare l' `ItemGroup` elemento che contiene `EmbeddedResource` gli elementi.  
  
6. Nell' `EmbeddedResource` elemento che chiama VSPackage. en-US. resx, sostituire l' `ManifestResourceName` elemento con un `LogicalName` elemento, impostare su `VSPackage.en-US.Resources` , come indicato di seguito.  
  
    ```xml  
    <EmbeddedResource Include="VSPackage.en-US.resx">  
      <MergeWithCTO>true</MergeWithCTO>  
      <LogicalName>VSPackage.en-US.Resources</LogicalName>  
    </EmbeddedResource>  
    ```  
  
7. Per ogni lingua localizzata, copiare l'  `EmbeddedResource` elemento per VSPackage. en-US e impostare l'attributo **include** e l'elemento **LogicalName** della copia nelle impostazioni locali di destinazione, come illustrato nell'esempio seguente.  
  
8. Per ogni elemento localizzato `VSCTCompile` , aggiungere un `ResourceName` elemento a cui punta `Menus.ctmenu` , come illustrato nell'esempio seguente.  
  
    ```xml  
    <ItemGroup>  
      <VSCTCompile Include="LocalizedPackage.es-ES.vsct">  
        <ResourceName>Menus.ctmenu</ResourceName>  
      </VSCTCompile>  
    </ItemGroup>  
    ```  
  
9. Salvare il file di progetto e ricaricare il progetto.  
  
10. Compilare il progetto.  
  
     Viene creato un assembly principale e gli assembly di risorse per ogni lingua. Per informazioni sulla localizzazione del processo di distribuzione, vedere [localizzazione di pacchetti VSIX](../extensibility/localizing-vsix-packages.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Estensione di menu e comandi](../extensibility/extending-menus-and-commands.md)   
 [Confronto tra oggetti MenuCommand e OleMenuCommands](../misc/menucommands-vs-olemenucommands.md)   
 [Globalizzazione e localizzazione](https://msdn.microsoft.com/library/9a59696b-d89b-45bd-946d-c75da4732d02)
