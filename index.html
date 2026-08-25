const colors = [
  {id: 1, name: "ホワイト", hex: "#FFFFFF"},
  {id: 2, name: "ブラック", hex: "#000000"},
  {id: 3, name: "グレー", hex: "#808080"},
  {id: 4, name: "ライトグレー", hex: "#D3D3D3"},
  {id: 5, name: "レッド", hex: "#FF0000"},
  {id: 6, name: "ワインレッド", hex: "#800000"},
  {id: 7, name: "ピンク", hex: "#FFC0CB"},
  {id: 8, name: "コーラル", hex: "#FF7F50"},
  {id: 9, name: "オレンジ", hex: "#FFA500"},
  {id: 10, name: "ライトオレンジ", hex: "#FFD580"},
  {id: 11, name: "イエロー", hex: "#FFFF00"},
  {id: 12, name: "ライトイエロー", hex: "#FFFFE0"},
  {id: 13, name: "ネオンイエロー", hex: "#CCFF00"},
  {id: 14, name: "グリーン", hex: "#008000"},
  {id: 15, name: "ライトグリーン", hex: "#90EE90"},
  {id: 16, name: "ミントブルー", hex: "#98FFFC"},
  {id: 17, name: "ターコイズ", hex: "#40E0D0"},
  {id: 18, name: "アクア", hex: "#00FFFF"},
  {id: 19, name: "ブルー", hex: "#0000FF"},
  {id: 20, name: "コバルトブルー", hex: "#0047AB"},
  {id: 21, name: "スカイブルー", hex: "#87CEEB"},
  {id: 22, name: "ネイビー", hex: "#000080"},
  {id: 23, name: "パープル", hex: "#800080"},
  {id: 24, name: "ラベンダー", hex: "#E6E6FA"},
  {id: 25, name: "ブラウン", hex: "#A52A2A"},
  {id: 26, name: "ライトブラウン", hex: "#D2B48C"},
  {id: 27, name: "ベージュ", hex: "#F5F5DC"},
  {id: 28, name: "サンドベージュ", hex: "#C2B280"},
  {id: 29, name: "ゴールド", hex: "#FFD700"},
  {id: 30, name: "シルバー", hex: "#C0C0C0"},
  {id: 31, name: "オリーブ", hex: "#808000"},
  {id: 32, name: "ブライトピンク", hex: "#FF69B4"},
  {id: 33, name: "ワインピンク", hex: "#C71585"}
];

let aiRecipe = [];
let manualRecipe = [];
let selectedColorId = 1;
let aiInfoCache = {};

document.getElementById('aiDate').valueAsDate = new Date();

const optionsList = document.getElementById('optionsList');
colors.forEach(c => {
  const div = document.createElement('div');
  div.className = 'option-item';
  div.onclick = () => selectColor(c.id);
  const borderColor = (c.hex === '#FFFFFF' || c.hex === '#FFFFE0' || c.hex === '#FFFF00') ? '#ccc' : '#e5e7eb';
  div.innerHTML = `
    <div class="option-color" style="background: ${c.hex}; border-color: ${borderColor};"></div>
    <span>${c.name} (${c.hex})</span>
  `;
  optionsList.appendChild(div);
});

function toggleOptions() {
  optionsList.classList.toggle('show');
}

function selectColor(colorId) {
  selectedColorId = colorId;
  const color = colors.find(c => c.id === colorId);
  document.getElementById('selectedColorText').textContent = `${color.name} (${color.hex})`;
  const indicator = document.getElementById('colorIndicator');
  indicator.style.background = color.hex;
  const borderColor = (color.hex === '#FFFFFF' || color.hex === '#FFFFE0' || color.hex === '#FFFF00') ? '#ccc' : '#e5e7eb';
  indicator.style.borderColor = borderColor;
  optionsList.classList.remove('show');
}

document.addEventListener('click', (e) => {
  if (!e.target.closest('.custom-select')) {
    optionsList.classList.remove('show');
  }
});

const slider = document.getElementById('ratioSlider');
const ratioValue = document.getElementById('ratioValue');

slider.addEventListener('input', () => {
  ratioValue.textContent = slider.value + '%';
});

function copyPrompt() {
  const colorList = colors.map(c => `${c.name} (${c.hex})`).join('\n');
  const promptColorName = document.getElementById('promptColorName').value.trim();
  const targetColorLine = promptColorName || '（ここに作りたい色を書いてください。例: 深海ブルー、桜色、夕焼け など）';
  
  const prompt = `以下の33色カラーサンドから、指定した色の混色レシピを提案してください。

【重要】必ず以下の形式で1行のみ回答してください：
ホワイト70%, ライトイエロー15%, ラベンダー10%, ピンク5%

※カラーコード付きでも可：ホワイト(#FFFFFF)70%, ライトイエロー(#FFFFE0)15%
※表・箇条書き・説明文は不要です。上記形式のみで回答してください。

【色リスト】
${colorList}

【依頼する色】
${targetColorLine}`;

  navigator.clipboard.writeText(prompt).then(() => {
    showToast('✅ プロンプトをコピーしました！AIに貼り付けて依頼してください');
  }).catch(() => {
    showToast('❌ コピーに失敗しました');
  });
}

function parseAIResponse() {
  const text = document.getElementById('pasteArea').value.trim();
  const date = document.getElementById('aiDate').value;
  const colorName = document.getElementById('aiColorName').value.trim() || '未設定';
  const aiName = document.getElementById('aiName').value;

  if (!text) {
    showToast('❌ 提案が空です');
    return;
  }

  if (!date) {
    showToast('❌ 日付を入力してください');
    return;
  }

  aiRecipe = [];

  const items = text.split(',').map(s => s.trim());

  items.forEach(item => {
    const match = item.match(/([ぁ-んァ-ヶー一-龠a-zA-Z]+(?:\s*[ぁ-んァ-ヶー一-龠a-zA-Z]+)*)(?:\s*\(#[0-9A-Fa-f]{6}\))?\s*(\d+)%?/);

    if (match) {
      const colorNameMatch = match[1].trim().replace(/\s+/g, '');
      const ratio = parseInt(match[2]);

      let color = colors.find(c => {
        const cleanColorName = c.name.replace(/\s+/g, '');
        return cleanColorName === colorNameMatch;
      });

      if (!color) {
        const sortedColors = [...colors].sort((a, b) => b.name.length - a.name.length);
        color = sortedColors.find(c => {
          const cleanColorName = c.name.replace(/\s+/g, '');
          return cleanColorName.includes(colorNameMatch) ||
                 colorNameMatch.includes(cleanColorName);
        });
      }

      if (color && ratio > 0) {
        aiRecipe.push({ color, ratio });
      }
    }
  });

  if (aiRecipe.length === 0) {
    showToast('❌ 提案を認識できませんでした。「色名 数字%」の形式で入力してください');
    return;
  }

  aiInfoCache = { date, colorName, aiName };
  updateAIResult(date, colorName, aiName);
  updateCompareAI();
  showToast('✨ AI提案を反映しました！');
}

function updateAIResult(date, colorName, aiName) {
  const resultHex = mixColors(aiRecipe);
  if (!resultHex) return;

  document.getElementById('displayDate').textContent = date;
  document.getElementById('displayColorName').textContent = colorName;
  document.getElementById('displayAiName').textContent = aiName;

  document.getElementById('aiColorDisplay').style.background = resultHex;
  document.getElementById('aiHexCode').textContent = resultHex;

  const recipeSection = document.getElementById('aiRecipeSection');
  recipeSection.innerHTML = '<div class="recipe-title">📋 レシピ:</div>';

  aiRecipe.forEach(item => {
    const div = document.createElement('div');
    div.className = 'recipe-item-display';
    const borderColor = (item.color.hex === '#FFFFFF' || item.color.hex === '#FFFFE0' || item.color.hex === '#FFFF00') ? '#ccc' : '#e5e7eb';
    div.innerHTML = `
      <div class="recipe-color-box" style="background: ${item.color.hex}; border-color: ${borderColor};"></div>
      <span class="recipe-text">${item.color.name}</span>
      <span class="recipe-percent">${item.ratio}%</span>
    `;
    recipeSection.appendChild(div);
  });

  document.getElementById('aiSummaryCard').style.display = 'block';
}

function copyAIInfo() {
  const resultHex = mixColors(aiRecipe);
  const recipeText = aiRecipe.map(item => `${item.color.name} ${item.ratio}%`).join('\n');

  const text = `📅 ${aiInfoCache.date}
🎨 ${aiInfoCache.colorName}
🤖 ${aiInfoCache.aiName}

📋 レシピ:
${recipeText}

🎨 ${resultHex}`;

  navigator.clipboard.writeText(text).then(() => {
    showToast('✅ AI提案情報をコピーしました！');
  }).catch(() => {
    showToast('❌ コピーに失敗しました');
  });
}

function updateCompareAI() {
  const resultHex = mixColors(aiRecipe);
  if (!resultHex) return;

  document.getElementById('compareAiColor').style.background = resultHex;
  document.getElementById('compareAiColor').innerHTML = `<span class="hex-code" style="font-size: 14px; color: white; text-shadow: 1px 1px 2px rgba(0,0,0,0.5);">${resultHex}</span>`;
  document.getElementById('compareAiHex').textContent = resultHex;
}

function updateCompareManual() {
  const resultHex = mixColors(manualRecipe);
  if (!resultHex) return;

  document.getElementById('compareManualColor').style.background = resultHex;
  document.getElementById('compareManualColor').innerHTML = `<span class="hex-code" style="font-size: 14px; color: white; text-shadow: 1px 1px 2px rgba(0,0,0,0.5);">${resultHex}</span>`;
  document.getElementById('compareManualHex').textContent = resultHex;
}

function addColor() {
  const color = colors.find(c => c.id === selectedColorId);
  const ratio = parseInt(slider.value);

  const existing = manualRecipe.find(item => item.color.id === color.id);
  if (existing) {
    existing.ratio += ratio;
  } else {
    manualRecipe.push({ color, ratio });
  }

  updateManualRecipeDisplay();
  updateCompareManual();
  updateManualSummary();
}

function updateManualRecipeDisplay() {
  const list = document.getElementById('manualRecipeList');
  list.innerHTML = '';

  if (manualRecipe.length === 0) {
    return;
  }

  manualRecipe.forEach((item, idx) => {
    const div = document.createElement('div');
    div.className = 'recipe-item';
    const borderColor = (item.color.hex === '#FFFFFF' || item.color.hex === '#FFFFE0' || item.color.hex === '#FFFF00') ? '#ccc' : '#e5e7eb';
    div.innerHTML = `
      <div class="recipe-left">
        <div class="color-preview" style="background: ${item.color.hex}; border-color: ${borderColor};"></div>
        <span class="recipe-name">${item.color.name}</span>
        <span class="recipe-percent-text">${item.ratio}%</span>
      </div>
      <button class="btn-remove" onclick="removeColor(${idx})">削除</button>
    `;
    list.appendChild(div);
  });
}

function updateManualSummary() {
  if (manualRecipe.length === 0) {
    document.getElementById('manualSummaryCard').style.display = 'none';
    return;
  }

  const resultHex = mixColors(manualRecipe);
  if (!resultHex) return;

  const today = new Date().toLocaleDateString('ja-JP');
  document.getElementById('manualDisplayDate').textContent = today;

  document.getElementById('manualColorDisplay').style.background = resultHex;
  document.getElementById('manualHexCode').textContent = resultHex;

  const recipeSection = document.getElementById('manualRecipeSection');
  recipeSection.innerHTML = '<div class="recipe-title">📋 レシピ:</div>';

  manualRecipe.forEach(item => {
    const div = document.createElement('div');
    div.className = 'recipe-item-display';
    const borderColor = (item.color.hex === '#FFFFFF' || item.color.hex === '#FFFFE0' || item.color.hex === '#FFFF00') ? '#ccc' : '#e5e7eb';
    div.innerHTML = `
      <div class="recipe-color-box" style="background: ${item.color.hex}; border-color: ${borderColor};"></div>
      <span class="recipe-text">${item.color.name}</span>
      <span class="recipe-percent">${item.ratio}%</span>
    `;
    recipeSection.appendChild(div);
  });

  document.getElementById('manualSummaryCard').style.display = 'block';
}

function copyManualInfo() {
  const resultHex = mixColors(manualRecipe);
  const recipeText = manualRecipe.map(item => `${item.color.name} ${item.ratio}%`).join('\n');
  const today = new Date().toLocaleDateString('ja-JP');

  const text = `✋ 手動調整の結果
📅 ${today}

📋 レシピ:
${recipeText}

🎨 ${resultHex}`;

  navigator.clipboard.writeText(text).then(() => {
    showToast('✅ 手動調整情報をコピーしました！');
  }).catch(() => {
    showToast('❌ コピーに失敗しました');
  });
}

function copyManualForAI() {
  const recipeText = manualRecipe.map(item => `${item.color.name}${item.ratio}%`).join(', ');

  navigator.clipboard.writeText(recipeText).then(() => {
    showToast('✅ AI入力用にコピーしました！AI提案欄に貼り付けてください');
  }).catch(() => {
    showToast('❌ コピーに失敗しました');
  });
}

function removeColor(idx) {
  manualRecipe.splice(idx, 1);
  updateManualRecipeDisplay();
  if (manualRecipe.length > 0) {
    updateCompareManual();
    updateManualSummary();
  } else {
    resetManualDisplay();
  }
}

function mixColors(recipe) {
  if (recipe.length === 0) return null;

  let r = 0, g = 0, b = 0;
  const total = recipe.reduce((sum, item) => sum + item.ratio, 0);

  recipe.forEach(item => {
    const hex = item.color.hex;
    const weight = item.ratio / total;
    r += parseInt(hex.slice(1, 3), 16) * weight;
    g += parseInt(hex.slice(3, 5), 16) * weight;
    b += parseInt(hex.slice(5, 7), 16) * weight;
  });

  r = Math.round(r);
  g = Math.round(g);
  b = Math.round(b);

  return '#' + [r, g, b].map(x => x.toString(16).padStart(2, '0')).join('').toUpperCase();
}

function resetManualDisplay() {
  document.getElementById('compareManualColor').style.background = '#cccccc';
  document.getElementById('compareManualColor').innerHTML = '<span class="hex-code" style="font-size: 14px;">-</span>';
  document.getElementById('compareManualHex').textContent = '追加してください';
  document.getElementById('manualSummaryCard').style.display = 'none';
}

function resetManual() {
  manualRecipe = [];
  updateManualRecipeDisplay();
  resetManualDisplay();
}

function saveAsHTML() {
  const htmlContent = document.documentElement.outerHTML;
  const blob = new Blob([htmlContent], { type: 'text/html;charset=utf-8' });
  const link = document.createElement('a');
  link.href = URL.createObjectURL(blob);
  link.download = 'カラーサンド混色シミュレーター.html';
  link.click();
  showToast('💾 ツールを保存しました！ファイルアプリから開けます');
}

function showToast(msg) {
  const toast = document.getElementById('toast');
  toast.textContent = msg;
  toast.classList.add('show');
  setTimeout(() => toast.classList.remove('show'), 3500);
}
