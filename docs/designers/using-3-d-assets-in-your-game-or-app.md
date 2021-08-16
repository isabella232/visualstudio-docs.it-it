---
title: Uso degli asset 3D nel gioco o nell'app
description: Informazioni su come usare Visual Studio elaborare asset 3D e includerli nelle compilazioni. Visual Studio personalizzazioni della compilazione per ogni asset prodotto.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- VC.Project.ImageContentTask.ContentOutput
- VC.Project.MeshContentTask.ContentOutput
- VC.Project.ImageContentTask.GeneratePremultipliedAlpha
- VC.Project.ImageContentTask.Compress
- VC.Project.ShaderGraphContentTask.ContentOutput
- VC.Project.ImageContentTask.GenerateMips
ms.assetid: ea587909-e434-46a8-abf8-9b3e95a58b4f
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-designers
ms.workload:
- multiple
ms.openlocfilehash: e4b173542659197472bcf99844d749d6992849cbc8a84db257da26ef05415b44
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121452966"
---
# <a name="how-to-use-3d-assets-in-your-game-or-app"></a>Procedura: Usare asset 3D nel gioco o nell'app

Questo articolo spiega come usare Visual Studio per elaborare gli asset 3D e includerli nelle build.

Dopo aver creato gli asset 3D mediante gli strumenti disponibili in Visual Studio, è possibile usarli nell'app. Perché sia possibile usare gli asset, è tuttavia necessario convertirli in un formato supportato da DirectX. Per agevolare la conversione degli asset, Visual Studio fornisce personalizzazioni di compilazione per ogni tipo di asset che può produrre. Per includere gli asset nella build, è sufficiente configurare il progetto per l'uso delle personalizzazioni di compilazione, aggiungere gli asset al progetto e configurarli per l'uso della personalizzazione di compilazione appropriata. In seguito è possibile caricare gli asset nell'app e usarli mediante la creazione e compilazione di risorse DirectX, come per qualsiasi altra app DirectX.

## <a name="configure-your-project"></a>Configurare il progetto

Prima di distribuire gli asset 3D nell'ambito della build, è necessario indicare a Visual Studio quali tipi di asset si intende distribuire. Visual Studio prevede già molti tipi di file comuni, ma dato che gli asset 3D sono usati solo da alcuni tipi di app, Visual Studio non presume che un progetto includerà questi tipi di file. Per indicare a Visual Studio che l'app usa questi tipi di asset, è possibile usare le *personalizzazioni di build* (file che indicano a Visual Studio come elaborare diversi tipi di file in modo utile) specificate per ogni tipo di asset. Dato che queste personalizzazioni vengono applicate a livello di singoli progetti, è sufficiente aggiungere le personalizzazioni appropriate al progetto.

### <a name="to-add-the-build-customizations-to-your-project"></a>Per aggiungere personalizzazioni di compilazione al progetto

1. In **Esplora soluzioni** aprire il menu di scelta rapida del progetto, quindi scegliere **Dipendenze di compilazione** > **Personalizzazioni compilazioni**.

   Verrà visualizzata la finestra di dialogo **File di personalizzazione compilazioni di Visual C++**.

2. In **File di personalizzazione compilazioni disponibili** selezionare le caselle di controllo corrispondenti ai tipi di asset da includere nel progetto, come indicato nella tabella seguente:

    |Tipo di asset|Nome personalizzazione di compilazione|
    |----------------| - |
    |Trame e immagini|**ImageContentTask(.targets, .props)**|
    |Modelli 3D|**MeshContentTask(.targets, .props)**|
    |Shader|**ShaderGraphContentTask(.targets, .props)**|

3. Fare clic su **OK** .

## <a name="include-assets-in-your-build"></a>Inclusione degli asset nella build

Dopo aver specificato i diversi tipi di asset 3D che si intende usare nel progetto, il passaggio successivo consiste nell'indicare quali file sono asset 3D e di quali tipi di asset si tratta.

### <a name="to-add-an-asset-to-your-build"></a>Per aggiungere un asset alla build

1. In **Esplora soluzioni** all'interno del progetto aprire il menu di scelta rapida di un asset, quindi scegliere **Proprietà**.

   Verrà visualizzata la finestra di dialogo **Pagina delle proprietà** relativa all'asset.

2. Verificare che le proprietà **Configurazione** e **Piattaforma** siano impostate sui valori a cui applicare le modifiche.

3. In **Proprietà di configurazione** scegliere **Generale**, quindi nella sezione **Generale** della griglia delle proprietà impostare la proprietà **Tipo di elemento** sul tipo di elemento della pipeline di contenuti appropriato. Ad esempio, per un file di immagine o trama, scegliere **Image Content Pipeline**(Pipeline di contenuti immagine).

    > [!IMPORTANT]
    > Per impostazione predefinita, Visual Studio presuppone che sia necessario suddividere in categorie molti tipi di file di immagine mediante il tipo di elemento **Immagine** integrato in Visual Studio. È quindi necessario modificare la proprietà **Tipo di elemento** di ogni immagine che deve essere elaborata dalla pipeline di contenuti immagine. Per altri tipi di file di origine della pipeline di contenuti per i modelli 3D e la grafica visual shader, viene usato il **Tipo di elemento** corretto per impostazione predefinita.

4. Fare clic su **OK** .

Di seguito sono indicati i tre tipi di elemento della pipeline di contenuti e i relativi tipi di file di origine e output.

|Item Type|Tipi di file di origine|Tipi di file di output|
|---------------| - | - |
|**Pipeline di contenuti immagine**|Portable Network Graphics (*.png*)<br /><br /> JPEG (*.jpg*, *.jpeg*, *.jpe*, *.jfif*)<br /><br /> Direct Draw Surface (*.dds*)<br /><br /> Graphics Interchange Format (*.gif*)<br /><br /> Bitmap (*.bmp*, *.dib*)<br /><br /> Tagged Image File Format (*.tif,* *.tiff*)<br /><br /> Targa (*.tga*)|DirectDraw Surface (*.dds*)|
|**Pipeline di contenuti mesh**|AutoDesk FBX Interchange File (*.fbx*)<br /><br /> Collada DAE File (*.dae*)<br /><br /> Wavefront OBJ File (*.obj*)|File mesh 3D (*.cmo*)|
|**Pipeline di contenuti shader**|Visual Shader Graph (*.dgsl*)|Output shader compilato (*con estensione cso*)|

## <a name="configure-asset-content-pipeline-properties"></a>Configurazione delle proprietà della pipeline di contenuti degli asset

È possibile impostare le proprietà della pipeline di contenuti di ogni file di asset in modo da costruirla in un modo specifico.

### <a name="to-configure-content-pipeline-properties"></a>Per configurare le proprietà della pipeline di contenuti degli asset

1. In **Esplora soluzioni** all'interno del progetto aprire il menu di scelta rapida per il file di asset, quindi scegliere **Proprietà**.

   Verrà visualizzata la finestra di dialogo **Pagina delle proprietà** relativa all'asset.

2. Verificare che le proprietà **Configurazione** e **Piattaforma** siano impostate sui valori a cui applicare le modifiche.

3. In **Proprietà di configurazione** scegliere il nodo della pipeline di contenuti, ad esempio **Pipeline di contenuti immagine** per gli asset di trama e immagine, quindi nella griglia delle proprietà impostare le proprietà sui valori appropriati. Ad esempio, per generare mipmap per un asset trama in fase di compilazione, impostare la proprietà **Genera MIP** su **Sì**.

4. Fare clic su **OK** .

### <a name="image-content-pipeline-configuration"></a>Configurazione della pipeline di contenuti immagine

Quando si usa lo strumento della pipeline di contenuti immagine per generare un asset trama, è possibile comprimere la trama in diversi modi, specificare se i livelli MIP devono essere generati in fase di compilazione e cambiare il nome del file di output.

|Proprietà|Descrizione|
|--------------|-----------------|
|**Comprimere**|Specifica il tipo di compressione usato per il file di output.<br /><br /> Le opzioni disponibili sono:<br /><br /> -   **Nessuna compressione**<br />-   **BC1_UNORM compressione**<br />-   **Compressione BC1_UNORM_SRGB**<br />-   **BC2_UNORM compressione**<br />-   **Compressione BC2_UNORM_SRGB**<br />-   **BC3_UNORM compressione**<br />-   **Compressione BC3_UNORM_SRGB**<br />-   **Compressione BC4_UNORM**<br />-   **Compressione BC4_SNORM**<br />-   **Compressione BC5_UNORM**<br />-   **Compressione BC5_SNORM**<br />-   **Compressione BC6H_UF16**<br />-   **Compressione BC6H_SF16**<br />-   **Compressione BC7_UNORM**<br />-   **Compressione BC7_UNORM_SRGB**<br /><br /> Per informazioni sui formati di compressione supportati nelle varie versioni di DirectX, vedere la [ Guida alla programmazione per DXGI](/windows/win32/direct3ddxgi/dx-graphics-dxgi-overviews).|
|Converti in formato premoltiplicato per alfa|**Sì** per convertire l'immagine in formato premoltiplicato per alfa nel file di output, altrimenti **No**. Viene modificato solo il file di output, mentre l'immagine di origine resta invariata.|
|**Genera MIP**|**Sì** per generare una catena MIP completa in fase di compilazione e includerla nel file di output, altrimenti **No**. Se si sceglie **No** e il file di origine contiene già una catena mipmap, nel file di output sarà presente una catena MIP. In caso contrario, non sarà presente alcuna catena MIP.|
|**Output contenuto**|Specifica il nome del file di output. **Importante:** la modifica dell'estensione del nome del file di output non influisce sul formato di file originale.|

### <a name="mesh-content-pipeline-configuration"></a>Configurazione della pipeline di contenuti mesh

Quando si usa lo strumento della pipeline di contenuti mesh per generare un asset mesh, è possibile cambiare il nome del file di output.

|Proprietà|Descrizione|
|--------------|-----------------|
|**Output contenuto**|Specifica il nome del file di output. **Importante:** la modifica dell'estensione del nome del file di output non influisce sul formato di file originale.|

### <a name="shader-content-pipeline-configuration"></a>Configurazione della pipeline di contenuti shader

Quando si usa lo strumento della pipeline di contenuti shader per generare un asset shader, è possibile cambiare il nome del file di output.

|Proprietà|Descrizione|
|--------------|-----------------|
|**Output contenuto**|Specifica il nome del file di output. **Importante:** la modifica dell'estensione del nome del file di output non influisce sul formato di file originale.|

## <a name="load-and-use-3d-assets-at-run-time"></a>Caricamento e uso di asset 3D in fase di esecuzione

### <a name="use-textures-and-images"></a>Uso di trame e immagini

Direct3D dispone di funzioni per la creazione di risorse di trama. In Direct3D 11 la libreria di utilità D3DX11 fornisce funzioni aggiuntive per la creazione di risorse trama e visualizzazioni di risorse direttamente dai file di immagine. Per altre informazioni su come creare una risorsa trama in Direct3D 11, vedere l'argomento relativo alle [trame](/windows/win32/direct3d11/overviews-direct3d-11-resources-textures). Per altre informazioni su come usare la libreria D3DX11 per creare una risorsa trama o una visualizzazione risorse da un file di immagine, vedere [How to: Initialize a texture from a file](/windows/win32/direct3d11/overviews-direct3d-11-resources-textures-how-to) (Procedura: Inizializzare una trama da un file).

### <a name="use-3d-models"></a>Uso di modelli 3D

Direct3D 11 non fornisce funzioni per la creazione di risorse da modelli 3D. È invece necessario scrivere un codice che legge il file del modello 3D e crea buffer di vertici e indici che rappresentano il modello 3D e le risorse richieste dal modello, ad esempio trame o shader, ad esempio trame o shader.

### <a name="use-shaders"></a>Uso degli shader

Direct3D fornisce funzioni per la creazione di risorse shader e per la relativa associazione alla pipeline di grafica programmabile. Per altre informazioni su come creare una risorsa shader in Direct3D e associarla alla pipeline, vedere [Programming guide for HLSL](/windows/win32/direct3dhlsl/dx-graphics-hlsl-pguide) (Guida alla programmazione per HLSL).

Nella pipeline di grafica programmabile, ogni fase della pipeline deve fornire alla fase successiva un risultato che sia formattato in modo tale da essere comprensibile. Dato che la finestra di progettazione shader può solo creare i pixel shader, spetta all'app verificare che i dati che riceve siano nel formato previsto. Il pixel shader è preceduto da molte fasi di shader programmabili che eseguono trasformazioni geometriche, ovvero vertex shader, hull shader, domain shader e geometry shader. Il pixel shader è preceduto anche dalla fase del mosaico non programmabile. Indipendentemente da quale sia la fase che precede immediatamente il pixel shader, deve fornire il risultato in questo formato:

```hlsl
struct PixelShaderInput
{
    float4 pos : SV_POSITION;
    float4 diffuse : COLOR;
    float2 uv : TEXCOORD0;
    float3 worldNorm : TEXCOORD1;
    float3 worldPos : TEXCOORD2;
    float3 toEye : TEXCOORD3;
    float4 tangent : TEXCOORD4;
    float3 normal : TEXCOORD5;
};
```

A seconda dei nodi della finestra di progettazione shader usati nello shader, può essere necessario fornire anche dati supplementari nel formato appropriato in base alle seguenti definizioni:

```hlsl
Texture2D Texture1 : register( t0 );
Texture2D Texture2 : register( t1 );
Texture2D Texture3 : register( t2 );
Texture2D Texture4 : register( t3 );
Texture2D Texture5 : register( t4 );
Texture2D Texture6 : register( t5 );
Texture2D Texture7 : register( t6 );
Texture2D Texture8 : register( t7 );

TextureCube CubeTexture1 : register( t8 );
TextureCube CubeTexture2 : register( t9 );
TextureCube CubeTexture3 : register( t10 );
TextureCube CubeTexture4 : register( t11 );
TextureCube CubeTexture5 : register( t12 );
TextureCube CubeTexture6 : register( t13 );
TextureCube CubeTexture7 : register( t14 );
TextureCube CubeTexture8 : register( t15 );

SamplerState TexSampler : register( s0 );

cbuffer MaterialVars : register (b0)
{
    float4 MaterialAmbient;
    float4 MaterialDiffuse;
    float4 MaterialSpecular;
    float4 MaterialEmissive;
    float MaterialSpecularPower;
};

cbuffer LightVars : register (b1)
{
    float4 AmbientLight;
    float4 LightColor[4];
    float4 LightAttenuation[4];
    float3 LightDirection[4];
    float LightSpecularIntensity[4];
    uint IsPointLight[4];
    uint ActiveLights;
}

cbuffer ObjectVars : register(b2)
{
    float4x4 LocalToWorld4x4;
    float4x4 LocalToProjected4x4;
    float4x4 WorldToLocal4x4;
    float4x4 WorldToView4x4;
    float4x4 UVTransform4x4;
    float3 EyePosition;
};

cbuffer MiscVars : register(b3)
{
    float ViewportWidth;
    float ViewportHeight;
    float Time;
};
```

## <a name="related-topics"></a>Argomenti correlati

|Titolo|Descrizione|
|-----------|-----------------|
|[Procedura: Esportare una trama che contiene mipmap](../designers/how-to-export-a-texture-that-contains-mipmaps.md)|Descrive come usare la pipeline di contenuti immagine per esportare una trama che contiene le mipmap precalcolate.|
|[Procedura: Esportare una trama con alfa premoltimullied](../designers/how-to-export-a-texture-that-has-premultiplied-alpha.md)|Descrive come usare la pipeline di contenuti immagine per esportare una trama che contiene valori premoltiplicati per alfa.|
|[Procedura: Esportare una trama da usare con app Direct2D o JavaScript](../designers/how-to-export-a-texture-for-use-with-direct2d-or-javascipt-apps.md)|Descrive come usare la pipeline di contenuti immagine per esportare una trama che può essere usata in un'app Direct2D o JavaScript.|
|[Uso di asset 3D per giochi e app](../designers/working-with-3-d-assets-for-games-and-apps.md)|Descrive gli strumenti di modifica forniti da Visual Studio per la creazione e la manipolazione di asset 3D, tra cui trame e immagini, modelli 3D e shader.|
|[Procedura: Esportare uno shader](../designers/how-to-export-a-shader.md)|Descrive come esportare uno shader dalla finestra di progettazione shader.|
