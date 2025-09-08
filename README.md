# Cloudflare CAPTCHA 解决方案  
[![Promo](https://github.com/bright-cn/Awesome-Web-Scraping/blob/main/Proxies%20and%20scrapers%20GitHub%20bonus%20banner%20CN.png)](https://bright.cn)

轻松利用 Bright Data 的先进 CAPTCHA 解决技术绕过 Cloudflare CAPTCHA。通过机器学习算法、[自动化 IP 轮换](https://bright.cn/solutions/rotating-proxies)以及强大的代理网络基础设施，确保无缝且稳定地访问目标网站。  
Bright Data 的 CAPTCHA Solver 是 [**Scraping Browser**](https://bright.cn/products/scraping-browser) 和 [**Web Unlocker API**](https://bright.cn/products/web-unlocker) 的内置功能，可完整应对最复杂的 CAPTCHA 挑战。

## 功能特色  
- **快速解决 CAPTCHA**：自动且高效地解决 Cloudflare CAPTCHA，准确度高。  
- **IP 轮换**：通过自动重试和动态 IP 调整来避免封禁。  
- **浏览器指纹**：模拟真实用户活动，绕过复杂的机器人检测
- **JavaScript 渲染**：处理 JavaScript 密集型网站的动态内容。  
- **全球地域覆盖**：精准解锁全球任意地区的内容。  
- **无缝集成**：与 Puppeteer、Playwright、Selenium 等工具轻松兼容。  
- **事件监控**：跟踪 CAPTCHA 解决事件，如检测、成功或失败。

## 为什么选择 Cloudflare CAPTCHA 解决方案  
### **全球 20,000+ 客户的信赖**  
Bright Data 的 CAPTCHA Solver 因其卓越的可靠性与性能，深受开发者、企业及各大机构的信赖。  

### **由高级代理网络提供支持**  
拥有超过 1 亿个 IP 地址及先进的地理定位功能，我们的代理基础设施可确保顺畅且不中断地解决 CAPTCHA。  

### **基于 AI 的 CAPTCHA 解决方案**  
我们的 CAPTCHA Solver 使用先进的 AI 逻辑来自动检测、分析并解决 CAPTCHA，可处理重试、指纹及请求头，绕过最复杂的反机器人措施。  

### **为开发者而生**  
- 与 Puppeteer、Playwright、Selenium 无缝集成。  
- 可完全自定义验证码解题行为。  
- 自动重试和动态 IP 调整，确保数据采集无间断。  

> **专家提示 💡**  
>> 已经有自己的 CAPTCHA 解决方案？可配合我们为 [Puppeteer](https://bright.cn/integration/puppeteer)、[Playwright](https://bright.cn/integration/playwright) 及 [Selenium](https://bright.cn/integration/selenium) 提供的代理服务，以减少 CAPTCHA 带来的干扰。

## 工作原理  
Bright Data 的 CAPTCHA Solver 集成在 **Scraping Browser** 和 **Web Unlocker** 中，让您轻松无忧地处理各种 CAPTCHA。  

### **自动化 CAPTCHA 解决**  
CAPTCHA Solver 会在实时环境中自动检测并解决 CAPTCHA，只需启用该功能即可完成从检测到解决的所有流程。  

### **Cloudflare 挑战的自定义选项**  
```javascript
// Define default options for different CAPTCHA types
function getCaptchaOptions(captchaType, customOptions = {}) {
  const defaultOptions = {
    timeout: 30000, // 最大等待时间 (毫秒) 用于解决 CAPTCHA
    check_timeout: 500, // 以毫秒为单位的间隔，用于检查 CAPTCHA 状态
    wait_networkidle: { timeout: 1000 }, // 网络空闲后等待 1 秒
    debug: false // 调试模式（默认关闭）
  };
  // Define CAPTCHA-specific selectors
  const captchaSelectors = {
    DataDome: { selector: '#datadome-captcha', success_selector: '#captcha-success' },
    reCAPTCHA: { selector: '.g-recaptcha', success_selector: '.recaptcha-success' },
    ClickCaptcha: { selector: '.click-captcha', success_selector: '.captcha-passed' },
    hCaptcha: { selector: '.h-captcha', success_selector: '.hcaptcha-success' },
    PerimeterX: { selector: '#px-captcha', success_selector: '#px-success' },
    SimpleCaptcha: { selector: '.simple-captcha', success_selector: '.captcha-done' },
    FunCaptcha: { selector: '.funcaptcha', success_selector: '.funcaptcha-success' },
    CloudflareTurnstile: { selector: '.cf-turnstile', success_selector: '.cf-success' },
    AWSWAF: { selector: '#aws-waf-captcha', success_selector: '#aws-waf-success' },
    GeeTest: { selector: '.geetest-captcha', success_selector: '.geetest-success' },
    KeyCAPTCHA: { selector: '#keycaptcha', success_selector: '#keycaptcha-success' },
    PuzzleCAPTCHA: { selector: '.puzzle-captcha', success_selector: '.puzzle-solved' },
    YandexCAPTCHA: { selector: '#yandex-captcha', success_selector: '#yandex-success' },
    ImageCAPTCHA: { selector: '.image-captcha', success_selector: '.image-captcha-success' },
    TextCAPTCHA: { selector: '.text-captcha', success_selector: '.text-captcha-success' }
  };
  // Get the correct selectors for the given CAPTCHA type
  const selectedOptions = captchaSelectors[captchaType] || {};
  // Merge default options with selected CAPTCHA-specific options and any custom overrides
  return { ...defaultOptions, ...selectedOptions, ...customOptions };
}
// Example usage for different CAPTCHA types
const ddOptions = getCaptchaOptions('DataDome', { timeout: 40000, debug: true });
const recaptchaOptions = getCaptchaOptions('reCAPTCHA', { debug: true });
const hcaptchaOptions = getCaptchaOptions('hCaptcha');
console.log(ddOptions);
console.log(recaptchaOptions);
console.log(hcaptchaOptions);
// Example error handling
try {
  if (!document.querySelector(ddOptions.selector)) {
    throw new Error(`未使用选择器找到 CAPTCHA 元素: ${ddOptions.selector}`);
  }
  // 在此处编写你的 CAPTCHA 解决逻辑
  solveCaptcha(ddOptions);
} catch (error) {
  console.error('解决 CAPTCHA 失败：', error.message);
}
```
#### 示例工作流程：  
1. **检测 CAPTCHA**：系统识别出 CAPTCHA 类型（例如 Cloudflare）。  
2. **解决 CAPTCHA**：使用 AI 逻辑自动解决 CAPTCHA。  
3. **失败重试**：如果解决失败，系统会自动在新 IP 上重试。  
4. **返回结果**：解决成功后，系统即可无缝访问目标网站。  

## 支持的 CAPTCHA 类型  
Bright Data 的 CAPTCHA Solver 支持多种 CAPTCHA 类型，包括：  
- [**DataDome**](https://bright.cn/products/web-unlocker/captcha-solver/datadome)  
- [**reCAPTCHA**](https://bright.cn/products/web-unlocker/captcha-solver/recaptcha)  
- [**Click Captcha**](https://bright.cn/products/web-unlocker/captcha-solver/click-captcha)  
- [**Cloudflare**](https://bright.cn/products/web-unlocker/captcha-solver/Cloudflare)  
- [**PerimeterX**](https://www.bright.cn/products/web-unlocker/captcha-solver/perimeterx)  
- [**SimpleCaptcha**](https://bright.cn/products/web-unlocker/captcha-solver/simplecaptcha)  
- [**FunCaptcha**](https://bright.cn/products/web-unlocker/captcha-solver/funcaptcha)  
- [**Cloudflare Turnstile**](https://www.bright.cn/products/web-unlocker/captcha-solver/cloudflare-turnstile)  
- [**AWS WAF Captcha**](https://www.bright.cn/products/web-unlocker/captcha-solver/aws-waf-captcha)  
- [**GeeTest CAPTCHA**](https://www.bright.cn/products/web-unlocker/captcha-solver/geetest-captcha)  
- [**KeyCAPTCHA**](https://bright.cn/products/web-unlocker/captcha-solver/keycaptcha)  
- [**Puzzle CAPTCHA**](https://bright.cn/products/web-unlocker/captcha-solver/puzzle-captcha)  
- [**Yandex CAPTCHA**](https://bright.cn/products/web-unlocker/captcha-solver/yandex-captcha)  
- [**Image CAPTCHA**](https://www.bright.cn/products/web-unlocker/captcha-solver/image-captcha)  
- [**Text CAPTCHA**](https://bright.cn/products/web-unlocker/captcha-solver/text-captcha)  

## 高级自定义  
[Bright Data 的 CAPTCHA Solver](https://github.com/luminati-io/Captcha-solver) 提供高级自定义选项，可根据特定需求微调解题逻辑。  

## **事件监控**  
跟踪 CAPTCHA 解决事件，以满足高级用例：  
- `Captcha.detected`：检测到 CAPTCHA，开始解题。  
- `Captcha.solveFinished`：成功解决 CAPTCHA。  
- `Captcha.solveFailed`：CAPTCHA 解决失败。  

## **价格**  
| **方案**          | **价格 (每 1K 结果)** | **月度费用**     | **描述**                                 |  
|-------------------|-----------------------|-----------------|------------------------------------------|  
| **按需付费**      | $1.50                | 无承诺          | 适合临时爬取需求。                       |  
| **Growth**        | $1.27                | $499            | 专为成长型团队打造。                     |  
| **Business**      | $1.12                | $999            | 适合大规模爬取操作。                     |  
| **Premium**       | $1.05                | $1,999          | 提供高级功能及优先支持。                 |  
| **Enterprise**    | 自定义报价           | 联系我们        | 面向顶级业务需求的定制化方案。           |  

🚀 **特别优惠**：首次充值可享受最高 **$500** 等额配对！  

## **为什么开发者钟爱 Cloudflare CAPTCHA 解决方案**  
- **简单易用的集成**：与 Puppeteer、Playwright、Selenium 无缝兼容。  
- **先进的 AI 逻辑**：自动处理重试、CAPTCHA 解题、指纹、IP 轮换及高级请求头。  
- **内置浏览器**：无需管理用于 JavaScript 渲染的外部浏览器。  
- **实时洞察**：通过实时仪表板监测网络性能。  
- **无与伦比的支持**：24/7 全球客服，且新功能不断更新。  

## **常见问题**  
### **Cloudflare CAPTCHA Solver 的工作原理是什么？**  
该方案使用先进的 AI 逻辑自动检测并解决 Cloudflare CAPTCHA。  

### **能够同时处理多个 CAPTCHA 吗？**  
可以。该方案能够同时处理多种 CAPTCHA，确保访问流畅不中断。  

### **如果 CAPTCHA 解决失败，该怎么办？**  
系统会自动进行重试。如果问题持续，请联系我们 24/7 的支持团队进行排查。  

---  

## **告别 Cloudflare CAPTCHA 的烦恼**  
立即开始免费试用，体验 Bright Data 带来的无缝 [Cloudflare Turnstile CAPTCHA 解决](https://www.bright.cn/products/web-unlocker/captcha-solver/cloudflare-turnstile)！
