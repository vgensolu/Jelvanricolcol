# DNS Configuration Guide for jelvanricolcol.pro

This guide explains how to configure your DNS settings to link your subdomain and email services with this website.

## Overview

- **Primary Domain**: jelvanricolcol.pro
- **Website**: https://jelvanricolcol.pro (hosted on GitHub Pages)
- **Email**: hr@jelvanricolcol.pro

## Step 1: Configure GitHub Pages Custom Domain

The CNAME file in this repository is already configured with `jelvanricolcol.pro`. GitHub Pages will automatically handle this once DNS is properly configured.

## Step 2: DNS Configuration at Your Domain Registrar

You need to configure the following DNS records at your domain registrar (e.g., Namecheap, GoDaddy, Cloudflare, etc.):

### For Website Hosting (GitHub Pages)

Add the following **A Records** for the apex domain (@):

```
Type: A
Host: @
Value: 185.199.108.153
TTL: Automatic or 3600

Type: A
Host: @
Value: 185.199.109.153
TTL: Automatic or 3600

Type: A
Host: @
Value: 185.199.110.153
TTL: Automatic or 3600

Type: A
Host: @
Value: 185.199.111.153
TTL: Automatic or 3600
```

Add a **CNAME Record** for www subdomain:

```
Type: CNAME
Host: www
Value: vgensolu.github.io
TTL: Automatic or 3600
```

### For Email Service (hr@jelvanricolcol.pro)

You have several options for setting up the hr@jelvanricolcol.pro email:

#### Option 1: Email Forwarding (Simplest)

Most domain registrars offer free email forwarding. Configure email forwarding to redirect:
- From: hr@jelvanricolcol.pro
- To: your-existing-email@gmail.com (or any email you currently use)

**How to set up:**
1. Log into your domain registrar
2. Find "Email Forwarding" or "Email Management"
3. Add forwarding rule: `hr@jelvanricolcol.pro` → `your-email@gmail.com`

#### Option 2: MX Records for Email Hosting

If you want to use a professional email service (Google Workspace, Microsoft 365, Zoho Mail, etc.):

**Example for Google Workspace:**
```
Type: MX
Host: @
Value: ASPMX.L.GOOGLE.COM
Priority: 1
TTL: 3600

Type: MX
Host: @
Value: ALT1.ASPMX.L.GOOGLE.COM
Priority: 5
TTL: 3600

Type: MX
Host: @
Value: ALT2.ASPMX.L.GOOGLE.COM
Priority: 5
TTL: 3600
```

**Note:** You'll need to sign up for the email service and use their specific MX records.

#### Option 3: Subdomain Email (hr.jelvanricolcol.pro)

If you want to use a subdomain like `hr.jelvanricolcol.pro` for a separate service:

```
Type: CNAME
Host: hr
Value: your-service.com
TTL: 3600
```

OR

```
Type: A
Host: hr
Value: [IP address of your service]
TTL: 3600
```

### For Email Authentication (Recommended)

Add these records to improve email deliverability and security:

**SPF Record:**
```
Type: TXT
Host: @
Value: v=spf1 include:_spf.google.com ~all
TTL: 3600
```
(Adjust the include value based on your email provider)

**DMARC Record:**
```
Type: TXT
Host: _dmarc
Value: v=DMARC1; p=none; rua=mailto:hr@jelvanricolcol.pro
TTL: 3600
```

**DKIM Record:**
Your email provider will provide this. It typically looks like:
```
Type: TXT
Host: default._domainkey
Value: v=DKIM1; k=rsa; p=[long key provided by email service]
TTL: 3600
```

## Step 3: Verify Configuration

### Website Verification
1. Wait 24-48 hours for DNS propagation (can be faster, sometimes minutes)
2. Visit https://jelvanricolcol.pro
3. Check that the website loads correctly
4. Verify SSL certificate is active (padlock icon in browser)

### Email Verification
1. Send a test email to hr@jelvanricolcol.pro
2. Verify it's received at your forwarding destination (if using forwarding)
3. Send an email FROM hr@jelvanricolcol.pro (if using email hosting)
4. Use tools like https://mxtoolbox.com/ to verify MX records

### DNS Propagation Check
Use these tools to check if DNS records have propagated:
- https://dnschecker.org/
- https://www.whatsmydns.net/
- Command line: `nslookup jelvanricolcol.pro`

## Troubleshooting

### Website not loading
- **Issue**: DNS records not propagated
  - **Solution**: Wait up to 48 hours, clear browser cache
  
- **Issue**: Incorrect GitHub Pages configuration
  - **Solution**: Go to GitHub repository Settings → Pages → Custom domain, ensure it shows "DNS check successful"

### Email not working
- **Issue**: MX records not configured
  - **Solution**: Add proper MX records for your email provider
  
- **Issue**: Email forwarding not set up
  - **Solution**: Configure forwarding at domain registrar
  
- **Issue**: SPF/DKIM/DMARC issues
  - **Solution**: Verify authentication records are properly configured

### SSL Certificate Issues
- GitHub Pages automatically provisions SSL certificates
- If certificate shows error, remove and re-add custom domain in GitHub Settings
- Wait a few minutes for certificate to provision

## Popular Domain Registrars Configuration Links

- **Namecheap**: Dashboard → Domain List → Manage → Advanced DNS
- **GoDaddy**: My Products → Domains → DNS Management
- **Cloudflare**: Dashboard → DNS → Records
- **Google Domains**: My domains → Manage → DNS
- **Porkbun**: Account → Domain Management → DNS

## Summary Checklist

- [ ] Add A records pointing to GitHub Pages IPs
- [ ] Add CNAME record for www subdomain
- [ ] Configure CNAME file in GitHub repository (already done)
- [ ] Set up email forwarding OR configure MX records
- [ ] Add SPF, DKIM, and DMARC records for email security
- [ ] Wait for DNS propagation (up to 48 hours)
- [ ] Test website access at https://jelvanricolcol.pro
- [ ] Test email delivery to hr@jelvanricolcol.pro
- [ ] Verify SSL certificate is active

## Need Help?

If you encounter issues:
1. Check your domain registrar's documentation for DNS configuration
2. Use DNS checking tools to verify records are set correctly
3. Contact your domain registrar's support if records aren't updating
4. For GitHub Pages issues, see: https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site

## Additional Resources

- [GitHub Pages Custom Domain Documentation](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site)
- [GitHub Pages IP Addresses](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/managing-a-custom-domain-for-your-github-pages-site)
- [DNS Record Types Explained](https://www.cloudflare.com/learning/dns/dns-records/)
- [Email Authentication Best Practices](https://www.cloudflare.com/learning/email-security/dmarc-dkim-spf/)

---

Last Updated: 2025-11-22
