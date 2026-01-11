# Septic Shock Perfusion Analyzer (SPA)

[![License: GPL v3](https://img.shields.io/badge/License-GPLv3-blue.svg)](https://www.gnu.org/licenses/gpl-3.0)
[![Version](https://img.shields.io/badge/version-2.1-green.svg)]()
[![Medical Tool](https://img.shields.io/badge/type-Clinical%20Decision%20Support-red.svg)]()

> **A cognitive decision support tool for ICU residents to assess peripheral perfusion in septic shock patients**

## 🎯 Overview

The Septic Shock Perfusion Analyzer (SPA) is an offline web-based Clinical Decision Support System (CDSS) designed to assist healthcare professionals in assessing peripheral perfusion parameters in patients with septic shock. This tool implements evidence-based guidelines from the ANDROMEDA-SHOCK trial and recent European research to provide real-time clinical recommendations.

### Key Features

- 📊 **Multi-parameter Assessment**: CRT, mottling score, temperature gradients, PPI, MAP, and lactate
- ⏱️ **Built-in CRT Timer**: Standardized measurement with automatic calculation
- 🌡️ **Automatic Gradient Calculation**: No mental math required - just enter temperatures
- 🔄 **Clinical Decision Algorithm**: Step-by-step guidance following evidence-based protocols
- 📋 **Multi-format Export**: Copy assessments as TXT, CSV, or TSV for EMR systems
- 💾 **Local History**: Track patient trends over time (stores last 50 assessments)
- 📱 **Mobile-Optimized**: Works on phones, tablets, and desktops
- 🔒 **Privacy-First**: All data stored locally - nothing transmitted to servers
- 🌐 **Offline-Ready**: Works without internet after initial load

## 🚀 Quick Start

### Option 1: Direct Use
1. Download `SPA-v2.1.html`
2. Open in any modern browser (Chrome, Firefox, Safari, Edge, Opera)
3. Start assessing patients immediately

### Option 2: Self-Hosted
```bash
# Clone the repository
git clone https://github.com/yourusername/septic-shock-perfusion-analyzer.git

# Navigate to directory
cd septic-shock-perfusion-analyzer

# Open in browser or serve with any web server
python -m http.server 8000
# Then visit http://localhost:8000
```

## 📖 How to Use

### 1. Patient Assessment Tab

#### Step 1: Enter Patient Information
- **Patient ID**: First name and case number (e.g., "Anand, 16F2026/001234")
- **CRT**: Use the built-in timer or enter manually
- **Mottling Score**: Visual assessment (0-5 scale)

#### Step 2: Temperature Measurements
Instead of calculating gradients manually:
- Enter **Forearm Temperature** (°C)
- Enter **Fingertip Temperature** (°C)
- App automatically calculates and interprets **Tskin-diff**

Similarly for central-peripheral gradient:
- Enter **Central/Tympanic Temperature** (°C)
- Enter **Great Toe Temperature** (°C)
- App automatically calculates and interprets **Tc-toe**

#### Step 3: Additional Parameters
- **PPI/PI**: From SpO₂ monitor display
- **MAP**: Current mean arterial pressure (mmHg)
- **Lactate**: Most recent value (mmol/L)

#### Step 4: Analyze
Click **"Analyze & Generate Recommendations"** to get:
- Color-coded interpretation of all parameters
- Risk level assessment (Low/Moderate/High)
- Evidence-based clinical recommendations
- Detection of hemodynamic dissociation

#### Step 5: Export to EMR
Choose your format:
- **📋 Copy as Text**: For narrative clinical notes
- **📋 Copy as CSV**: For spreadsheet tracking
- **📋 Copy as TSV**: For EMR systems accepting tab-delimited data

### 2. CRT Timer Tab

Standardized capillary refill time measurement:

1. Click **START**
2. Apply firm pressure to fingertip/earlobe with glass slide
3. Timer automatically prompts "RELEASE pressure NOW!" at 5 seconds
4. Press **STOP** when color returns
5. CRT automatically calculated and filled in assessment form

### 3. Quick Reference Guide Tab

Access normal values, measurement protocols, and clinical guidelines without leaving the app:
- Reference ranges for all parameters
- Step-by-step measurement techniques
- Resuscitation timing guidelines
- Red flags for hemodynamic dissociation

### 4. Algorithm Tab

Interactive clinical decision pathway:
- Step-by-step flowchart
- Clear decision points
- Evidence-based interventions at each stage

### 5. History Tab

- Review past assessments
- Track patient trends
- Color-coded risk levels
- Stores last 50 assessments locally

## 📊 Clinical Background

### Evidence Base

This tool implements guidelines from:

1. **ANDROMEDA-SHOCK Trial** (Hernández et al., JAMA 2019)
   - CRT-guided resuscitation non-inferior to lactate-guided
   - Reduces fluid administration in first 8 hours
   - Faster feedback loop than lactate clearance

2. **European Peripheral Perfusion Research** (Guo et al., Eur J Med Res 2024)
   - Early peripheral perfusion monitoring improves outcomes
   - Multi-parameter approach superior to single markers

3. **ICU Best Practices** (Ait-Oufella et al., Lima & Bakker)
   - Standardized CRT measurement techniques
   - Temperature gradient interpretation
   - Hemodynamic coherence principles

### Normal Values Reference

| Parameter | Normal | Abnormal | Clinical Significance |
|-----------|--------|----------|----------------------|
| CRT | < 3 sec | ≥ 3 sec | Impaired peripheral perfusion |
| Mottling | 0-2 | ≥ 3 | Predicts hemodynamic deterioration |
| Tskin-diff | 0.0-0.2°C | > 4.6°C | Peripheral vasoconstriction |
| Tc-toe | 5-7°C | ≥ 10°C | Systemic perfusion deficit |
| PPI | > 1.4 | < 0.7-1.4 | Risk of AKI, extubation failure |

## 🔧 Technical Details

### System Requirements
- Modern web browser (Chrome 90+, Firefox 88+, Safari 14+, Edge 90+)
- JavaScript enabled
- ~500 KB storage for local history
- No internet required after initial load

### Technology Stack
- Pure HTML5/CSS3/JavaScript
- No external dependencies
- No server required
- localStorage API for data persistence

### Browser Compatibility
- ✅ Chrome/Chromium
- ✅ Firefox
- ✅ Safari (iOS/macOS)
- ✅ Edge
- ✅ Opera
- ✅ Samsung Internet
- ✅ Brave

### Data Privacy
- **100% local processing** - no data transmitted to servers
- **localStorage only** - data never leaves device
- **HIPAA/GDPR compliant architecture** (user responsible for institutional policies)
- **No analytics or tracking**

## ⚠️ Important Disclaimers

### Not a Medical Device
This tool is a **Clinical Decision Support System (CDSS)** for educational and cognitive assistance purposes only. It has **NOT** been cleared or approved by the FDA, EMA, or any other regulatory body for use as a primary medical device.

### Clinical Judgment Required
- **NOT a substitute** for clinical judgment by qualified healthcare professionals
- All calculations must be **independently verified** against institutional standards
- Clinical decisions remain the responsibility of the treating physician

### Limitation of Liability
The authors and copyright holders are **NOT liable** for any claim, damages, or other liability arising from the use of this software. See [LICENSE](LICENSE) for full terms.

### Data Privacy Responsibility
Users are **solely responsible** for ensuring compliance with:
- Local patient data privacy laws (HIPAA, GDPR, etc.)
- Institutional IT policies
- Medical record documentation requirements

## 🤝 Contributing

We welcome contributions from the medical and developer communities!

### How to Contribute
1. Fork the repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

### Contribution Guidelines
- **Clinical accuracy first**: All changes must be evidence-based
- **Maintain simplicity**: Tool must remain usable during high-stress situations
- **Privacy by design**: No features that compromise data privacy
- **Cross-browser testing**: Ensure compatibility
- **Documentation**: Update README for any feature changes

### Reporting Issues
- Use GitHub Issues for bug reports
- Include browser version and steps to reproduce
- For clinical/medical questions, cite relevant literature

## 📚 References

1. Guo, Q., Liu, D., Wang, X. et al. Early peripheral perfusion monitoring in septic shock. *Eur J Med Res* 29, 477 (2024). [doi:10.1186/s40001-024-02074-1](https://doi.org/10.1186/s40001-024-02074-1)

2. Hernández G, et al. Effect of a Resuscitation Strategy Targeting Peripheral Perfusion Status vs Serum Lactate Levels on 28-Day Mortality Among Patients With Septic Shock: The ANDROMEDA-SHOCK Randomized Clinical Trial. *JAMA* 2019;321(7):654-664. [doi:10.1001/jama.2019.0071](https://doi.org/10.1001/jama.2019.0071)

3. Ait-Oufella H, et al. Capillary refill time exploration during septic shock. *Intensive Care Med* 2014;40(7):958-64. [doi:10.1007/s00134-014-3326-4](https://doi.org/10.1007/s00134-014-3326-4)

4. Lima A, Bakker J. Clinical assessment of peripheral circulation. *Curr Opin Crit Care* 2015;21(3):226-31. [doi:10.1097/MCC.0000000000000194](https://doi.org/10.1097/MCC.0000000000000194)

## 📄 License

This program is free software: you can redistribute it and/or modify it under the terms of the **GNU General Public License v3.0** as published by the Free Software Foundation.

**Copyright © 2026 Prof. Jyotirmay Kirtania**

This program is distributed in the hope that it will be useful, but **WITHOUT ANY WARRANTY**; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the [GNU General Public License](LICENSE) for more details.

## 👨‍⚕️ Author

**Prof. Jyotirmay Kirtania**
- Anesthesiologist
- Medical Teaching Faculty 
- Evidence-Based Medicine Advocate

## 🌟 Acknowledgments

- ICU residents and nurses for real-world feedback
- ANDROMEDA-SHOCK trial investigators
- Open-source medical software community
- All healthcare workers managing septic shock patients

## 📞 Support

- **Documentation**: See this README and in-app Guide tab
- **Issues**: Use GitHub Issues for bug reports
- **Discussions**: Use GitHub Discussions for questions
- **Updates**: Watch this repository for new versions

## 🗺️ Roadmap

### Version 2.2 (Planned)
- [ ] Multi-language support (Spanish, French, Mandarin)
- [ ] Dark mode for overnight shifts
- [ ] Print-friendly assessment reports
- [ ] Trend visualization graphs

### Version 3.0 (Future)
- [ ] Integration with FHIR-compatible EMR systems
- [ ] Machine learning risk prediction
- [ ] Multi-patient dashboard
- [ ] QR code sharing for rounds

## 📊 Version History

### v2.1 (Current - January 2026)
- ✅ Automatic temperature gradient calculation
- ✅ Multi-format export (TXT/CSV/TSV)
- ✅ Enhanced mobile responsiveness
- ✅ Local history tracking (50 assessments)
- ✅ Improved CRT timer with audio-visual cues

### v2.0
- ✅ Built-in CRT timer
- ✅ Clinical decision algorithm
- ✅ Quick reference guide
- ✅ History tracking

### v1.0
- ✅ Initial release
- ✅ Basic parameter assessment
- ✅ Recommendations engine

---

## 🔖 Citation

If you use this tool in research or education, please cite:
```bibtex
@software{kirtania2026spa,
  author = {Kirtania, Jyotirmay},
  title = {Septic Shock Perfusion Analyzer (SPA)},
  year = {2026},
  version = {2.1},
  license = {GPL-3.0},
  url = {https://github.com/yourusername/septic-shock-perfusion-analyzer}
}
```

---

### Patient Assessment Interface
*Clean, intuitive interface for rapid data entry during critical situations*

### CRT Timer
*Standardized measurement tool with visual and timing cues*

### Clinical Decision Algorithm
*Evidence-based flowchart for step-by-step guidance*

### Multi-format Export
*One-click copying to EMR in your preferred format*

---

## 🎓 Training & Education

### For Residents
- Use the **Guide tab** as a quick reference during rounds
- Practice with the **CRT timer** to standardize technique
- Review **History** to track learning progression

### For Educators
- Demonstrate evidence-based sepsis management
- Show real-time decision-making with the algorithm
- Use as a teaching tool during bedside rounds

### For Institutions
- Standardize peripheral perfusion assessment across ICU teams
- Reduce variation in septic shock management
- Facilitate protocol adherence with built-in guidelines

---

## 🔐 Security & Privacy

### Data Storage
- **Client-side only**: All processing happens in your browser
- **No cloud sync**: Data never transmitted to external servers
- **localStorage**: Standard browser storage API (encrypted at OS level)

### Compliance Considerations
While the app architecture is privacy-preserving:
- Check institutional policies before use
- Verify compliance with local regulations (HIPAA, GDPR, etc.)
- Consider device security (lock screens, encryption)
- Be mindful of shoulder surfing in public areas

### Recommendations
- Use on institutional devices when possible
- Clear history when using shared devices
- Don't include full patient identifiers if screenshotting
- Follow your hospital's mobile device policies

---

## 🐛 Known Issues & Limitations

### Technical Limitations
- Requires JavaScript enabled
- localStorage limit (~5-10 MB depending on browser)
- No cloud backup of assessment history
- Print layout could be improved (planned for v2.2)

### Clinical Limitations
- Cannot replace comprehensive hemodynamic assessment
- Temperature gradients affected by ambient conditions
- CRT subjective even with standardization
- Designed for septic shock (may not apply to other shock types)

### Workarounds
- Clear history periodically if approaching storage limit
- Export important assessments before clearing
- Always corroborate with other clinical parameters
- Use institutional protocols as primary reference

---

## 💬 FAQ

**Q: Is this approved for clinical use?**  
A: This is a CDSS tool, not a medical device. It assists but doesn't replace clinical judgment. Check with your institution.

**Q: Will my data be shared?**  
A: No. All data stays on your device. Nothing is transmitted to servers.

**Q: Can I use this on my personal phone?**  
A: Technically yes, but check institutional policies. Consider data privacy implications.

**Q: Does it work offline?**  
A: Yes! After initial load, it works completely offline.

**Q: Can I suggest new features?**  
A: Absolutely! Open a GitHub Issue with your suggestion and clinical rationale.

**Q: How often is it updated?**  
A: Major versions ~yearly. Bug fixes and minor updates as needed.

**Q: Can I modify it for my hospital?**  
A: Yes! GPL v3 license allows modification. Please share improvements back to the community.

**Q: What if I find a clinical error?**  
A: Please report immediately via GitHub Issues with references to correct it.

---

## 🌍 Language Support

Currently available in:
- 🇬🇧 English

Planned for v2.2:
- 🇪🇸 Spanish
- 🇫🇷 French
- 🇨🇳 Mandarin Chinese

Want to help translate? Email me at jyotirmay@mpmmcc.tmc.gov.in

---

## 🏥 Institutional Deployment

### For IT Departments

**Deployment Options:**
1. **Intranet hosting**: Place on internal web server
2. **Kiosk mode**: Load on dedicated tablets
3. **Bookmark distribution**: Share URL via internal email

**Technical Requirements:**
- Any HTTP server (Apache, Nginx, IIS)
- No database required
- No backend processing
- Static file hosting sufficient

**Security Considerations:**
- Consider Content Security Policy (CSP)
- HTTPS recommended but not required
- No external API calls to whitelist
- Review localStorage usage with security team

### Sample Nginx Configuration
```nginx
server {
    listen 80;
    server_name spa.yourhospital.local;
    
    root /var/www/septic-shock-perfusion-analyzer;
    index SPA-v2.1.html;
    
    location / {
        try_files $uri $uri/ =404;
    }
}
```

---

## 📧 Contact

- **Email**: [jyotirmay@mpmmcc.tmc.gov.in)

---

**⚕️ Made with care for ICU teams worldwide | 🛡️ Privacy-first design | 📖 Evidence-based medicine**

---

*Last updated: January 11, 2026*
