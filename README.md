### Giriş
Bu rehber, Story SDK kullanarak müziklerinizi IP olarak kaydetmenize ve NFT olarak mint etmenize yardımcı olmak için hazırlanmıştır. 


# Story ile İlk Adımlar: Hazırlık

Not: Bir önceki rehber olan https://github.com/Himess/story-protocol-guide yaptıysanız sadece ## 5. Suno ile Müzik Oluşturma , ## 6. Müzik NFT Resminizi Ipfs ‘ e kayıt etme. ve başlıklarına göz atmanız ve ## 13.2 Metadata Dosyalarını Ayarlayın kısmındaki değişiklikleri yapmanız yeterli olacaktır.


## 0.Test Cüzdan oluşturma ve Faucet Talep etme

Burası için bomboş bir metamask test cüzdanınızı kullanmanızı öneririm.
Cüzdanınızı oluşturduktan sonra
Sağ üstten üç noktaya tıklayıp hesap bilgilerine tıklayın.

![image](https://github.com/user-attachments/assets/e796eae9-3934-4430-8670-c5716b9b6184)

Daha sonra özel anahtarı göstere tıklayın ve size verdiği anahtarı bir not defterine kaydedin bize lazım olacak.

Bu aşamayı bitirdik şimdi bize Test IP lazım.

Bunun için https://faucet.story.foundation/ adresine gidip test IP talep etmeniz gerekmekte.
Gitcoin puanı gerekiyor. Main hesabınızdan alıp, test adresinize atabilirsiniz.
Ortalama 2-3 dakikaya test IP 'leriniz gelmiş olur.

Herşey hazırsa kuruluma başlayabiliriz.

---

## 1. Bir Çalışma Klasörü Oluşturun

Bilgisayarınızda bir klasör oluşturun. Örneğin: `StoryProject`. Bu klasörün içine tüm kodlarınızı ve dosyalarınızı ekleyeceğiz.

![image](https://github.com/user-attachments/assets/cc275a3e-386f-4832-8ba8-9281ee12be42)

---

## 2. Visual Studio Code (VS Code) Kurulumu

[VS Code](https://code.visualstudio.com/) web sitesine gidin ve işletim sisteminize uygun sürümü indirin.

1. İndirilen `.exe` dosyasını çalıştırın.
2. Lisans sözleşmesini kabul edin ve **Next** butonuna tıklayın.
3. Yükleme konumunu seçin (varsayılan yeri bırakabilirsiniz) ve **Next** butonuna tıklayın.
4. **Add to PATH** seçeneğini işaretleyin. Bu, VS Code'u terminalden çalıştırmanızı sağlar.
5. **Install** butonuna tıklayın ve kurulum tamamlanana kadar bekleyin.

Tebrikler, kurulum tamamlandı!

---

## 3. Gerekli Araçları Kurun

Story ile çalışmaya başlamak için aşağıdaki araçları bilgisayarınıza kurmanız gerekiyor:

### Node.js ve npm Kurulumu

[Node.js](https://nodejs.org/tr) web sitesine gidin ve **LTS (Long-Term Support)** sürümünü seçin.

![image](https://github.com/user-attachments/assets/e2a659e7-0c57-402a-a235-ffc3f00e39cb)

**Kurulum Adımları:**
1. İndirdiğiniz dosyayı çalıştırın.
2. Kurulumu **Next > Next** diyerek tamamlayın.
3. Ardından şu komutları terminale yazın ve çalıştırın:
   ```bash
   npm install -g ts-node
   npm install -g typescript

---

## 4. Visual Studio Code Uygulamasını Açın

Menüden File > Open Folder seçeneğine tıklayın ve oluşturduğunuz StoryProject adlı klasörü açın.

Daha sonra üst menüden Terminal > New Terminal seçeneğini tıklayın.

![image](https://github.com/user-attachments/assets/32ebc389-6810-488f-b05a-841e5c0d297e)

Node.js'in doğru şekilde yüklendiğini kontrol edin:

Terminale şu komutları yazın:
```bash
node -v
npm -v
```

Eğer şu şekilde çıktı alıyorsanız, kurulum başarılıdır:

![image](https://github.com/user-attachments/assets/9d39f4d7-0ce9-43fc-89ee-9412e2b99087)

---

## 5. Suno ile Müzik Oluşturma 🎵

Suno , istediğiniz bir kaç kelime ile size müzik oluşturmanızı sağlar. Biz de projemizde bunu kullanacağız.

https://suno.com/create?wid=default Adresine girin. Kayıt olduktan sonra,
Song description kısmına Ne tür bir müzik istediğinizle alakalı şeyler yazın. Müzik türünüz tamamen sizin hayal gücünüze kalmış. İster heyecan verici bir gitar solosu, ister yumuşak bir piyano tınısı diyebilirsiniz.

<img width="553" alt="SUNO" src="https://github.com/user-attachments/assets/723783a3-6173-4a06-8ba3-d486a80aa65b" />

Ben Celestine Sloth ‘ ların lazy ve uykulu olmaları hakkında şeyleri yazdım ve bana müziği üretti.
Gayet de beğendim açıkçası :D Rehber sonunda dinlemenizi tavsiye ederim.

Prompt girdikten sonra create ‘ e basın.
Daha sonra oluşturduğunuz müziğe tıklayın ve,

<img width="992" alt="Celestine Sloth's Lullaby" src="https://github.com/user-attachments/assets/15b85ee6-c42b-47d8-bd18-e4a350687919" />

Paylaş butonuna tıkladığınızda size link verecek,
Link bu şekilde olmalı,

`https://suno.com/song/eb448e54-4b1b-4558-966c-95dfb31b6b3d` gibi.
Burada size verdiği CID ‘ önemli. 

Mesela benimkinde 

`eb448e54-4b1b-4558-966c-95dfb31b6b3d`

Bu verdiği CID ‘ yi şu şekilde yazacağız. Örnek bu şekilde olmalı.


`https://cdn1.suno.ai/eb448e54-4b1b-4558-966c-95dfb31b6b3d.mp3`


Burası oldukça önemli burayı mutlaka düzgün bir biçimde yapmaya çalışın.

---

## 6. Müzik NFT Resminizi Ipfs ‘ e kayıt etme.

Bu adım oldukça basit. 
Pinata’ya geri dönüyoruz.
https://app.pinata.cloud/ipfs/files Sitesine gidiyoruz.


Buradan +Add ve ardından File Upload ‘ a basyıoruz.

<img width="1448" alt="Ekran Resmi 2025-01-27 01 09 26" src="https://github.com/user-attachments/assets/532d8e90-dd45-4afb-ba93-654d20f2cb05" />






![Pasted Graphic 4](https://github.com/user-attachments/assets/bbdf6b9d-7c0a-4733-bb62-596c5079783f)

Oluşturduğumuz dosyanın üzerine tıkladığımızda, Bize bu şekilde çıktı verecek,


`https://plum-conventional-cephalopod-536.mypinata.cloud/ipfs/bafkreifqjicmmnhianug4sgbainou66qcanhkhoyz2rhvnq2gcp6tegt54`


Burası çok önemli bunu ileride kullanacağız.
Eğer daha önce Pinata GateWays oluşturmadıysanız hata alırsınız. Yine arayüzden oluşturduktan sonra tekrar dönün.


---


## 7. Projeyi Başlatın

Aşağıdaki komutları çalıştırarak bir Node.js projesi başlatın:

```bash
npm init -y
```

Bu komut, projenizin kök dizininde bir `package.json` dosyası oluşturur.

Örnek çıktı şu şekilde olmalıdır:

![image](https://github.com/user-attachments/assets/cda37400-2da5-4736-a1ec-14e0bb3561f3)

---

## 8. `.env` Dosyası Oluşturun

Proje klasörünüzde `.env` adında bir dosya oluşturun. Bu dosya, özel anahtarlarınızı ve hassas bilgilerinizi saklamak için kullanılacak.

Adımlar:
1-VS Code içinde sağ tıklayın ve New File seçeneğini seçin.
2-Dosya adını `.env` olarak yazın ve Enter tuşuna basın.
Şöyle görünecek:
![image](https://github.com/user-attachments/assets/9997e18c-85d1-4c64-a06c-bd4b52a73d03)


Sonuç şu şekilde olacaktır:

![image](https://github.com/user-attachments/assets/049c1b5b-6d18-497e-8764-d8f8d5b3e22d)

---

## 9. Testnet Cüzdan Özel Anahtarını Ekleyin

Story Testnet cüzdan özel anahtarınızı `.env` dosyasına ekleyin. Bu özel anahtar, Story ağına bağlantı kurmanızı sağlar.

Örnek:
```bash
WALLET_PRIVATE_KEY=<YOUR_WALLET_PRIVATE_KEY>
Not: Özel anahtarınızı asla başkasıyla paylaşmayın. Yeni bir cüzdan oluşturmanızı öneririm.
```

Örnek Çıktı:
```bash
WALLET_PRIVATE_KEY=e12312312312312312312312312312312312312312312312312312312312312
```

---

## 10. Pinata API Anahtarı Ekleyin

Pinata, IPFS ağına dosya yüklemek için kullanılan bir araçtır. Pinata üzerinden bir hesap oluşturun ve bir API Key (JWT) oluşturun.
https://app.pinata.cloud/developers/api-keys ' e girin.
+ New Key butonuna tıklayın.
Aşağıdaki kutucukları işaretleyin:

![image](https://github.com/user-attachments/assets/f64181c3-8c0d-445f-ab9f-a48d995a8533)

Verdiği JWT anahtarını kaydedin ve `.env` dosyanıza ekleyin:
```bash
PINATA_JWT=<YOUR_PINATA_JWT>
```

Örnek:
```bash
PINATA_JWT=e12321431242141424
```

---

## 11. `.env` Dosyasını Güncelleme

1-RPC URL'sini `.env` dosyasına ekleyin.
2-NFT Contract Adresi ekleyin.
```bash
RPC_PROVIDER_URL=https://rpc.odyssey.storyrpc.io
NFT_CONTRACT_ADDRESS=0x041B4F29183317Fd352AE57e331154b73F8a1D73
```

Final `.env` Örneği:
```bash
WALLET_PRIVATE_KEY=e12312312312312312312312312312312312312312312312312312312312312
PINATA_JWT=e12321431242141424
RPC_PROVIDER_URL=https://rpc.odyssey.storyrpc.io
NFT_CONTRACT_ADDRESS=0x041B4F29183317Fd352AE57e331154b73F8a1D73
```

---

## 12. Gerekli Paketleri Kurun

Terminalde aşağıdaki komutu çalıştırarak projeniz için gerekli bağımlılıkları yükleyin:
```bash
npm install @story-protocol/core-sdk pinata-web3 viem
```

Kurulum tamamlandığında dosyalarınız şu şekilde görünecek:

![image](https://github.com/user-attachments/assets/38737bb1-65db-447a-a7e2-93c10047889f)

---

## 13. Proje Dosyalarını Yapılandırma

Bu adımda, Story SDK'yı kullanmak ve IP verilerini oluşturmak için bazı temel dosyaları yapılandıracağız.

### 13.1 `utils.ts` Dosyasını Oluşturun

Bu dosya, Story SDK yapılandırmanızı (`config`) ve istemcinizi (`client`) kurmak için kullanılacak.

1. Proje kök dizininde **`utils.ts`** adında bir dosya oluşturun.
2. Aşağıdaki kodu dosyaya yapıştırın:

```typescript
import { StoryClient, StoryConfig } from '@story-protocol/core-sdk';
import { http } from 'viem';
import { privateKeyToAccount, Address, Account } from 'viem/accounts';

// Çevresel değişkenleri kontrol edin
const privateKey: Address = `0x${process.env.WALLET_PRIVATE_KEY}`;
if (!privateKey) {
  throw new Error('WALLET_PRIVATE_KEY bulunamadı. Lütfen .env dosyanızı kontrol edin.');
}

const account: Account = privateKeyToAccount(privateKey);

const config: StoryConfig = {
  account: account,
  transport: http(process.env.RPC_PROVIDER_URL),
  chainId: 'odyssey',
};

const client = StoryClient.newClient(config);

export { client, account };
```

Sonuç şu şekilde görünecek:

![image](https://github.com/user-attachments/assets/6957e055-ab6a-45a3-9e04-95d52ce9f6b2)

---

## 13.2 Metadata Dosyalarını Ayarlayın

*Dikkat burada değişiklikler yapacağız.
IP ve NFT metadata bilgilerini oluşturacağız.

Proje kök dizininde `main.ts` adında bir dosya oluşturun.
Aşağıdaki kodu dosyaya yapıştırın:

```typescript
import { IpMetadata } from '@story-protocol/core-sdk';
import { client, account } from './utils';
import { uploadJSONToIPFS } from './uploadToIpfs';
import { createHash } from 'crypto';
import { Address } from 'viem';
import { mintNFT } from './mintNFT';

async function main() {
  // 1. IP Metadata oluştur
  const ipMetadata: IpMetadata = client.ipAsset.generateIpMetadata({
    title: 'Celestine Sloths Uyku Sesi',
    description: 'Celestine Sloths NFT topluluğuna özel uyku sesi kaydı.',
    watermarkImg: 'https://plum-conventional-cephalopod-536.mypinata.cloud/ipfs/bafkreifqjicmmnhianug4sgbainou66qcanhkhoyz2rhvnq2gcp6tegt54',
    ipType: 'Music',
    media: [
      {
        name: 'Celestine Uyku Sesi',
        url: 'https://cdn1.suno.ai/eb448e54-4b1b-4558-966c-95dfb31b6b3d.mp3',
        mimeType: 'audio/mpeg',
      },
    ],
    attributes: [
      {
        key: 'Artist',
        value: 'Celestine Sloths',
      },
      {
        key: 'Mood',
        value: 'Relaxing',
      },
      {
        key: 'Duration',
        value: '3:45',
      },
      {
        key: 'Source',
        value: 'Suno.com',
      },
    ],
    creators: [
      {
        name: 'Celestine Community',
        address: account.address,
        contributionPercent: 100,
      },
    ],
  });

  // 2. NFT Metadata oluştur
  const nftMetadata = {
    name: 'Celestine Sloths NFT',
    description: 'Celestine Sloths topluluğunun uyku sesi NFT\'si.',
    image: 'https://plum-conventional-cephalopod-536.mypinata.cloud/ipfs/bafkreifqjicmmnhianug4sgbainou66qcanhkhoyz2rhvnq2gcp6tegt54', // NFT için görsel URL'si
    media: [
      {
        name: 'Celestine Uyku Sesi',
        url: 'https://cdn1.suno.ai/eb448e54-4b1b-4558-966c-95dfb31b6b3d.mp3',
        mimeType: 'audio/mpeg',
      },
    ],
    attributes: [
      {
        key: 'Artist',
        value: 'Celestine Sloths',
      },
      {
        key: 'Mood',
        value: 'Relaxing',
      },
      {
        key: 'Duration',
        value: '3:45',
      },
      {
        key: 'Source',
        value: 'Suno.com',
      },
    ],
  };

  // 3. Metadata'ları IPFS'e yükle
  const ipIpfsHash = await uploadJSONToIPFS(ipMetadata);
  const ipHash = createHash('sha256').update(JSON.stringify(ipMetadata)).digest('hex');
  const nftIpfsHash = await uploadJSONToIPFS(nftMetadata);
  const nftHash = createHash('sha256').update(JSON.stringify(nftMetadata)).digest('hex');

  console.log('IP Metadata IPFS Hash:', ipIpfsHash);
  console.log('NFT Metadata IPFS Hash:', nftIpfsHash);

  // 4. NFT Mint Et
  const tokenId = await mintNFT(account.address, `https://ipfs.io/ipfs/${nftIpfsHash}`);
  if (!tokenId) {
    console.error('NFT mint işlemi başarısız oldu!');
    return;
  }

  console.log('Mint edilen NFT Token ID:', tokenId);

  // 5. NFT'yi IP Asset olarak kaydet
  const response = await client.ipAsset.registerIpAndAttachPilTerms({
    nftContract: process.env.NFT_CONTRACT_ADDRESS as Address,
    tokenId: tokenId,
    terms: [], // Özel IP şartlarını buraya ekleyebilirsiniz.
    ipMetadata: {
      ipMetadataURI: `https://ipfs.io/ipfs/${ipIpfsHash}`,
      ipMetadataHash: `0x${ipHash}`,
      nftMetadataURI: `https://ipfs.io/ipfs/${nftIpfsHash}`,
      nftMetadataHash: `0x${nftHash}`,
    },
    txOptions: { waitForTransaction: true },
  });

  console.log(`Transaction Hash: ${response.txHash}`);
  console.log(`IP Asset ID: ${response.ipId}`);
  console.log(`View on Explorer: https://explorer.story.foundation/ipa/${response.ipId}`);
}

main().catch((error) => {
  console.error('Bir hata oluştu:', error);
});
```

Buraya dikkat edelim, ## 5. Suno ile Müzik Oluşturma ve ## 6. Müzik NFT Resminizi Ipfs ‘ e kayıt etme. kısmındaki aldığınız 2 farklı linki değiştireceksiniz.

`https://cdn1.suno.ai/eb448e54-4b1b-4558-966c-95dfb31b6b3d.mp3`

Şeklindeki müzik kaydınız 

ve de 

`https://plum-conventional-cephalopod-536.mypinata.cloud/ipfs/bafkreifqjicmmnhianug4sgbainou66qcanhkhoyz2rhvnq2gcp6tegt54` 

Bu şekilde oluşturduğunuz NFT resminiz.


Benim size verdiğim `main.ts` de sırasıyla şu değişiklikleri yapıcaksınız, iki önemli değişiklik var.


Bu kısma watermarkImg: 
`https://plum-conventional-cephalopod-536.mypinata.cloud/ipfs/bafkreifqjicmmnhianug4sgbainou66qcanhkhoyz2rhvnq2gcp6tegt54`, 

yerine oluşturduğunuz NFT ıpfs linkini yazıcaksnız.

url: `https://cdn1.suno.ai/eb448e54-4b1b-4558-966c-95dfb31b6b3d.mp3`, 

yerine de kendi oluşturduğunuz müzik kaydını yazıcaksınız.

Geriye kalan yerler opsiyonel ama değiştirebilirsiniz.

Örnek olarak “Celestine” ile başlayan yerleri kendi istediğiniz şekilde değiştirebilirsiniz. Sizin kendi NFT isminizi “Doğa Sevgisi” yaptıysanız onunla alakalı şeyler ile doldurabilirsiniz.

Burayı tamamladıysanız geriye sadece copy paste atmanız kaldı. 

---

## 13.3 `uploadToIpfs.ts` Dosyasını Oluşturun
Proje kök dizininde `uploadToIpfs.ts` adında bir dosya oluşturun.
Aşağıdaki kodu dosyaya yapıştırın:

```typescript
import { PinataSDK } from 'pinata-web3';

const pinata = new PinataSDK({
  pinataJwt: process.env.PINATA_JWT,
});

export async function uploadJSONToIPFS(jsonMetadata: any): Promise<string> {
  const { IpfsHash } = await pinata.upload.json(jsonMetadata);
  return IpfsHash;
}
```

---

## 13.4 TypeScript ve tsconfig.json Ayarları

Proje dizininizde bir `tsconfig.json` dosyası oluşturun. İçerisine aşağıdaki ayarları ekleyin:

```json
{
  "compilerOptions": {
    "target": "ES6",
    "module": "CommonJS",
    "strict": true,
    "esModuleInterop": true,
    "moduleResolution": "node",
    "baseUrl": "./",
    "paths": {
      "*": ["node_modules/*"]
    }
  },
  "include": ["**/*.ts"],
  "exclude": ["node_modules"]
}
```

Sonuç şu şekilde görünmeli:

![image](https://github.com/user-attachments/assets/c06ddcb0-23a5-475b-a254-f53e6239d909)

---

## 14. Mint Fonksiyonunu Tanımlayın
Proje kök dizininde `mintNFT.ts` adlı bir dosya oluşturun ve aşağıdaki kodları ekleyin:

```typescript
import { http, createWalletClient, createPublicClient, Address } from 'viem';
import { privateKeyToAccount } from 'viem/accounts';
import { odyssey } from '@story-protocol/core-sdk';
import { account } from './utils';
import { defaultNftContractAbi } from './defaultNftContractAbi';

const baseConfig = {
  chain: odyssey,
  transport: http(process.env.RPC_PROVIDER_URL),
} as const;

export const publicClient = createPublicClient(baseConfig);
export const walletClient = createWalletClient({
  ...baseConfig,
  account,
});

export async function mintNFT(to: Address, uri: string): Promise<number | undefined> {
  const { request } = await publicClient.simulateContract({
    address: process.env.NFT_CONTRACT_ADDRESS as Address,
    functionName: 'mintNFT',
    args: [to, uri],
    abi: defaultNftContractAbi,
  });
  const hash = await walletClient.writeContract(request);
  const { logs } = await publicClient.waitForTransactionReceipt({
    hash,
  });
  if (logs[0].topics[3]) {
    return parseInt(logs[0].topics[3], 16);
  }
}
```

---

## 15. `defaultNftContractAbi.ts` Dosyasını Oluşturun

Proje kök dizininde `defaultNftContractAbi.ts` adında bir dosya oluşturun ve aşağıdaki kodu yapıştırın:

```typescript
export const defaultNftContractAbi = [
  {
    inputs: [
      {
        internalType: "address",
        name: "to",
        type: "address",
      },
      {
        internalType: "string",
        name: "uri",
        type: "string",
      },
    ],
    name: "mintNFT",
    outputs: [
      {
        internalType: "uint256",
        name: "tokenId",
        type: "uint256",
      },
    ],
    stateMutability: "nonpayable",
    type: "function",
  },
];
```

---

## 16. Projeyi Çalıştırma

Tüm dosyaları oluşturduktan sonra, projeyi terminalde çalıştırmak için aşağıdaki komutu kullanın:

```bash
ts-node main.ts
```

**Örnek Çıktı**
Projeyi başarıyla çalıştırdıktan sonra aşağıdaki gibi bir çıktı almalısınız:

IP Metadata IPFS Hash: bafkreica73k4b7kkmdkxjscvrqr3qprdfwv2hifp6kwdnoowrxumrczgvq
NFT Metadata IPFS Hash: bafkreih5dspmybxw4orleqxneztdmx6sjxrcypbotffpetorxb3vmhu7sq
Mint edilen NFT Token ID: 492
Transaction Hash: 0xc826f63c7bdb444fac7f5c31a94ef198c4004ab6109ee3c6be60b6cf9b511c3e
IP Asset ID: 0x3ce426e3376dA1786c18e487f280FD32A674F6F8
View on Explorer: https://explorer.story.foundation/ipa/0x3ce426e3376dA1786c18e487f280FD32A674F6F8


**Tebrikler! 🎉**
Projeyi başarıyla tamamladınız ve Müziğinizi Story IP üzerinde kayıt etmeyi başardınız.
