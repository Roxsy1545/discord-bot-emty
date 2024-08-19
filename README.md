```markdown
# Discord.js v14 Gelişmiş Bot Altyapısı

Bu proje, Discord.js v14 için gelişmiş bir bot altyapısıdır. Komutlar, eventler ve modüler yapıya sahip bu altyapı, bot geliştirmeyi kolaylaştırmak için tasarlanmıştır. Bu yapı, projeyi genişletmek isteyen geliştiriciler için mükemmel bir başlangıç noktasıdır.

## Başlarken

### Gereksinimler

- Node.js 16.9.0 veya üstü
- Discord.js v14
- `dotenv` modülü (Çevresel değişkenler için)

### Kurulum

1. Projeyi GitHub'dan klonlayın:

   ```bash
   git clone https://github.com/username/discord-bot.git
   ```

2. Proje dizinine gidin:

   ```bash
   cd discord-bot
   ```

3. Gerekli bağımlılıkları yükleyin:

   ```bash
   npm install
   ```

4. `config.json` dosyasını düzenleyin ve botunuzun `token`, `clientId` ve `guildId` bilgilerini ekleyin.

5. Botu başlatın:

   ```bash
   npm start
   ```

## Proje Yapısı

Proje aşağıdaki şekilde yapılandırılmıştır:

```plaintext
discord-bot/
├── node_modules/        # Node.js modülleri
├── commands/            # Slash komut dosyaları
│   └── ping.js
├── events/              # Event dosyaları
│   └── ready.js
│   └── interactionCreate.js
├── config.json          # Bot yapılandırma dosyası
├── index.js             # Ana giriş noktası
├── package.json         # Proje meta verileri ve bağımlılıklar
├── README.md            # Proje açıklamaları
└── .env                 # Çevresel değişkenler (isteğe bağlı)
```

### `commands/` Klasörü

Bu klasörde botunuzun komutları tanımlanır. Her komut bir `.js` dosyası olarak saklanır ve aşağıdaki yapıya sahip olmalıdır:

```javascript
const { SlashCommandBuilder } = require('discord.js');

module.exports = {
    data: new SlashCommandBuilder()
        .setName('komut_adı')
        .setDescription('Komut açıklaması'),
    async execute(interaction) {
        // Komut mantığı burada işlenir
    },
};
```

Örnek: `ping.js` komutu, botun gecikmesini kontrol etmek için basit bir komuttur.

### `events/` Klasörü

Bu klasörde botunuzun eventleri tanımlanır. Her event bir `.js` dosyası olarak saklanır ve botun belirli olaylara nasıl tepki vereceğini tanımlar:

- `ready.js`: Botun başlatıldığında çalıştırılır.
- `interactionCreate.js`: Slash komutları gibi etkileşimler oluştuğunda tetiklenir.

Her event dosyası şu şekilde yapılandırılmıştır:

```javascript
module.exports = {
    name: 'event_adı',
    once: true, // Bu event sadece bir kez mi çalışacak?
    async execute(...args) {
        // Event mantığı burada işlenir
    },
};
```

### Modüler Yapı

Bu altyapı, modüler bir yapıdadır. Bu, komutlar ve eventlerin ayrı dosyalara bölünerek daha düzenli bir yapı oluşturmasını sağlar. Yeni komutlar veya eventler eklemek için sadece ilgili klasöre yeni bir dosya oluşturmanız yeterlidir.

### Çevresel Değişkenler

`.env` dosyasını kullanarak bot tokeni gibi hassas bilgileri güvenli bir şekilde saklayabilirsiniz. `.env` dosyası örneği:

```
TOKEN=YOUR_BOT_TOKEN
CLIENT_ID=YOUR_CLIENT_ID
GUILD_ID=YOUR_GUILD_ID
```

Bu bilgileri `index.js` dosyasında `process.env` üzerinden çağırabilirsiniz.

### Lisans

Bu proje MIT Lisansı ile lisanslanmıştır. Daha fazla bilgi için `LICENSE` dosyasına bakın.
```

Bu içeriği README.md dosyanıza ekleyip GitHub'da paylaşabilirsiniz.
