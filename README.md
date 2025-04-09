# ProgramingLive

[![GitHub Pages](https://img.shields.io/badge/GitHub%20Pages-Online-brightgreen)](https://programinglive.github.io)
[![Ruby](https://img.shields.io/badge/Ruby-3.2.2-red)](https://ruby-lang.org)
[![Node.js](https://img.shields.io/badge/Node.js-18.16.0-blue)](https://nodejs.org)

## About ProgramingLive

ProgramingLive is a vibrant community platform dedicated to fostering a collaborative programming culture in Indonesia. We aim to transform the solitary nature of coding into an engaging, supportive experience where developers can learn, grow, and make a positive impact together.

## Mission

- **Empowerment**: Enable Indonesian developers to reach their full potential through knowledge sharing and collaboration
- **Community**: Build a supportive network where developers can learn from each other's experiences
- **Growth**: Provide resources and guidance for continuous learning and professional development
- **Impact**: Create meaningful contributions to Indonesia's technological landscape

## Features

- 📚 Comprehensive documentation and tutorials
- 🏗️ Project showcase and collaboration platform
- 🎥 Educational video content
- 📱 Mobile-responsive design
- 🔍 Advanced search functionality
- 📊 SEO-optimized content
- 📱 Responsive design for all devices

## Technical Stack

- **Frontend**: Jekyll with Just-the-Docs theme
- **Backend**: GitHub Pages
- **Dependencies**: Ruby, Node.js, and modern JavaScript tools
- **Build Tools**: Bundler, Yarn, and npm

## Project Structure

```
programinglive.github.io/
├── _config.yml          # Jekyll configuration
├── _includes/          # Template partials
├── _layouts/           # Page layouts
├── assets/             # Static assets
├── docs/               # Documentation content
├── pages/              # Main pages
├── project/            # Project showcase
├── tutorial/           # Tutorial content
├── youtube/            # Video content
└── sponsor/           # Sponsor information
```

## Security and Sensitive Files

### Handling ads.txt
The `ads.txt` file contains sensitive advertising configuration information. For development purposes, use the template file `ads.txt.example` and replace the values with your actual credentials.

1. Never commit your actual `ads.txt` file to version control
2. Use the template file for development: `ads.txt.example`
3. Keep your production `ads.txt` file in a secure location
4. Never share your advertising credentials publicly

### Security Best Practices

1. Never commit sensitive files to version control
2. Use environment variables for configuration when possible
3. Keep API keys, credentials, and sensitive information in secure locations
4. Regularly review and update security measures

## Getting Started

1. Clone the repository:
   ```bash
   git clone https://github.com/programinglive/programinglive.github.io.git
   ```

2. Install dependencies:
   ```bash
   bundle install
   npm install
   ```

3. Start the development server:
   ```bash
   bundle exec jekyll serve --livereload
   ```

4. The site will be available at: http://localhost:4000

## Contributing

We welcome contributions from the community! Please read our [Contributing Guidelines](CONTRIBUTING.md) before submitting pull requests.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Contact

For inquiries or support, please contact us at creative@programinglive.com