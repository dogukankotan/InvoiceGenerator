================
InvoiceGenerator
================
.. image:: https://travis-ci.org/creckx/InvoiceGenerator.svg
    :target: https://travis-ci.org/creckx/InvoiceGenerator

This is library to generate a simple PDF invoice. It's based on ReportLab.

THIS IS A CUSTOM FORK!
InvoiceGenerator for İşin Başı Reklam. Transformed to Receipts. Added TR locale.

Installation
============

Run this command as root::

	pip install git+https://github.com/dogukankotan/InvoiceGenerator.git

Example
=======

Usage::

	import os
    from InvoiceGenerator.api import Invoice, Item, Client, Provider, Creator
    from InvoiceGenerator.pdf import SimpleInvoice

    # choose en as language
    os.environ["INVOICE_LANG"] = "tr"

    client = Client('İşin Başı Reklam Bilgi Teknolojileri ve Ticaret A.Ş')
    client.address = 'GÜLBAHÇE GÜLBAHÇE CAD.NO:1/17'
    client.city = 'URLA/İZMİR'
    client.zip = '35000'
    client.vat_id = '4820575342'
    client.ir = 'Urla'
    provider = Provider('İşin Başı Reklam Bilgi Teknolojileri ve Ticaret A.Ş')
    provider.address = 'GÜLBAHÇE GÜLBAHÇE CAD.NO:1/17'
    provider.city = 'URLA/İZMİR'
    provider.zip = '35000'
    provider.vat_id = '4820575342'
    provider.ir = 'Urla'
    creator = Creator('Workif')

    invoice = Invoice(client, provider, creator)
    invoice.currency_locale = 'tr_TR.UTF-8'
    invoice.currency = '₺'
    invoice.date = '10-12-2017'
    invoice.number = '205123123112'
    invoice.add_item(Item(1, 1.24, description="Ödeme Hizmeti Komisyonu"))

    pdf = SimpleInvoice(invoice)
    pdf.gen("/Users/workif/PycharmProjects/InvoiceGenerator/test.pdf")

