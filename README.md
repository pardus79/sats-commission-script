# sats-commission-script
Script for calculating commission payments, in Bitcoin, from a Woocommerce store.

# Requirements:
Woocommerce Web Store with Plugin "Advanced Order Export For WooCommerce" (https://wordpress.org/plugins/woo-order-export-lite/) and BtcPayServer Plugin.

Products assigned to categories that signify who gets commissions. For example, if Bob receives commission for a shirt, assign that shirt to a subcategory corresponding to Bob. This script will calculate a flat % per category. So if Bob gets 50% commission for one item and 25% commission for another, assign them different product categories.

Windows OS

Python. Check if Python is installed by running in a Windows Command Prompt
```
python --version
```

Openpyxl. Run `pip list` to see if installed. If not listed, run to install:
```
pip install openpyxl
```

Download `commission.py` from this repository to any folder.

# Usage

In Woocommerce, access the Advanced Order Export for WooCommerce plugin. Click on the "Tools" tab. Paste the follwing into the "Import Settings" field and click "Import":
```
{
    "now": {
        "version": "2.0",
        "mode": "now",
        "title": "",
        "skip_empty_file": true,
        "log_results": false,
        "from_status": [],
        "to_status": [],
        "change_order_status_to": "",
        "statuses": [
            "wc-completed"
        ],
        "from_date": "",
        "to_date": "",
        "sub_start_from_date": "",
        "sub_start_to_date": "",
        "sub_end_from_date": "",
        "sub_end_to_date": "",
        "sub_next_paym_from_date": "",
        "sub_next_paym_to_date": "",
        "from_order_id": "",
        "to_order_id": "",
        "shipping_locations": [],
        "shipping_methods": [],
        "item_names": [],
        "item_metadata": [],
        "user_roles": [],
        "user_names": [],
        "user_custom_fields": [],
        "billing_locations": [],
        "payment_methods": [],
        "any_coupon_used": "0",
        "coupons": [],
        "order_custom_fields": [],
        "product_categories": [],
        "product_vendors": [],
        "products": [],
        "product_sku": "",
        "exclude_products": [],
        "product_taxonomies": [],
        "product_custom_fields": [],
        "product_attributes": [],
        "product_itemmeta": [],
        "format": "XLS",
        "format_xls_use_xls_format": "0",
        "format_xls_sheet_name": "Orders",
        "format_xls_display_column_names": "1",
        "format_xls_auto_width": "1",
        "format_xls_direction_rtl": "0",
        "format_xls_force_general_format": "0",
        "format_xls_remove_emojis": "0",
        "format_xls_row_images_width": "50",
        "format_xls_row_images_height": "50",
        "format_csv_enclosure": "\"",
        "format_csv_delimiter": ",",
        "format_csv_linebreak": "\\r\\n",
        "format_csv_display_column_names": "1",
        "format_csv_add_utf8_bom": "0",
        "format_csv_item_rows_start_from_new_line": "0",
        "format_csv_encoding": "UTF-8",
        "format_csv_delete_linebreaks": "0",
        "format_csv_remove_linebreaks": "0",
        "format_csv_force_quotes": "0",
        "format_tsv_linebreak": "\\r\\n",
        "format_tsv_display_column_names": "1",
        "format_tsv_add_utf8_bom": "0",
        "format_tsv_item_rows_start_from_new_line": "0",
        "format_tsv_encoding": "UTF-8",
        "format_xml_root_tag": "Orders",
        "format_xml_order_tag": "Order",
        "format_xml_product_tag": "Product",
        "format_xml_coupon_tag": "Coupon",
        "format_xml_prepend_raw_xml": "",
        "format_xml_append_raw_xml": "",
        "format_xml_self_closing_tags": "1",
        "format_xml_preview_format": "0",
        "format_json_start_tag": "[",
        "format_json_end_tag": "]",
        "format_json_unescaped_slashes": 0,
        "format_json_numeric_check": 0,
        "format_json_encode_unicode": 0,
        "format_pdf_display_column_names": "1",
        "format_pdf_repeat_header": "1",
        "format_pdf_direction_rtl": 0,
        "format_pdf_orientation": "L",
        "format_pdf_page_size": "A4",
        "format_pdf_font_size": "8",
        "format_pdf_header_text": "",
        "format_pdf_footer_text": "",
        "format_pdf_pagination": "C",
        "format_pdf_fit_page_width": "0",
        "format_pdf_cols_width": "25",
        "format_pdf_cols_align": "L",
        "format_pdf_cols_vertical_align": "T",
        "format_pdf_page_header_text_color": "#000000",
        "format_pdf_page_footer_text_color": "#000000",
        "format_pdf_table_header_text_color": "#000000",
        "format_pdf_table_header_background_color": "#FFFFFF",
        "format_pdf_table_row_text_color": "#000000",
        "format_pdf_table_row_background_color": "#FFFFFF",
        "format_pdf_logo_source_id": "0",
        "format_pdf_logo_source": "",
        "format_pdf_logo_width": "0",
        "format_pdf_logo_height": "15",
        "format_pdf_logo_align": "R",
        "format_pdf_row_images_width": "15",
        "format_pdf_row_images_height": "15",
        "format_pdf_row_images_add_link": "0",
        "format_pdf_row_dont_page_break_order_lines": "0",
        "format_html_display_column_names": "1",
        "format_html_repeat_header_last_line": "0",
        "format_html_font_size": "13",
        "format_html_header_text": "",
        "format_html_footer_text": "",
        "format_html_cols_align": "L",
        "format_html_header_text_color": "#000000",
        "format_html_footer_text_color": "#000000",
        "format_html_table_header_text_color": "#000000",
        "format_html_table_header_background_color": "#FFFFFF",
        "format_html_table_row_text_color": "#000000",
        "format_html_table_row_background_color": "#FFFFFF",
        "format_html_row_images_width": "100",
        "format_html_row_images_height": "100",
        "format_html_images_add_link": "0",
        "format_html_custom_css": "",
        "all_products_from_order": "0",
        "skip_refunded_items": "0",
        "skip_suborders": "0",
        "export_refunds": "0",
        "export_matched_items": "0",
        "date_format": "Y-m-d",
        "time_format": "H:i",
        "sort_direction": "DESC",
        "sort": "setup_field_string_plain_products_category",
        "format_number_fields": "0",
        "export_all_comments": "0",
        "export_refund_notes": "0",
        "strip_tags_product_fields": "0",
        "strip_html_tags": "0",
        "round_item_tax_rate": "0",
        "cleanup_phone": "0",
        "convert_serialized_values": "0",
        "enable_debug": "0",
        "billing_details_for_shipping": "0",
        "custom_php": "0",
        "custom_php_code": "",
        "mark_exported_orders": "0",
        "export_unmarked_orders": "0",
        "summary_report_by_products": "0",
        "duplicated_fields_settings": {
            "products": {
                "repeat": "rows",
                "populate_other_columns": "1",
                "max_cols": "10",
                "group_by": "product",
                "line_delimiter": "\\n"
            },
            "coupons": {
                "repeat": "rows",
                "max_cols": "10",
                "group_by": "product",
                "line_delimiter": "\\n"
            }
        },
        "summary_report_by_customers": "0",
        "order_fields": [
            {
                "segment": "common",
                "key": "order_date",
                "label": "Order Date",
                "format": "date",
                "colname": "Order Date"
            },
            {
                "segment": "products",
                "key": "products",
                "colname": "Products",
                "label": "Products",
                "format": "undefined"
            },
            {
                "segment": "products",
                "key": "plain_products_category",
                "label": "Category",
                "format": "string",
                "colname": "Category"
            },
            {
                "segment": "products",
                "key": "plain_products_name",
                "label": "Item Name",
                "format": "string",
                "colname": "Item Name"
            },
            {
                "segment": "products",
                "key": "plain_products_qty_minus_refund",
                "label": "Quantity (- Refund)",
                "format": "number",
                "colname": "Quantity (- Refund)",
                "sum": "1"
            },
            {
                "segment": "products",
                "key": "plain_products_item_price",
                "label": "Item Cost",
                "format": "money",
                "colname": "Item Cost",
                "sum": "1"
            },
            {
                "segment": "user",
                "key": "plain_orders_BTCPay_BTC-LightningNetwork_rate",
                "label": "BTCPay_BTC-LightningNetwork_rate",
                "format": "number",
                "colname": "btcusd"
            },
            {
                "segment": "coupons",
                "key": "coupons",
                "colname": "Coupons",
                "label": "Coupons",
                "format": "undefined"
            }
        ],
        "order_product_fields": [
            {
                "label": "SKU",
                "format": "string",
                "colname": "SKU",
                "default": 1,
                "key": "sku"
            },
            {
                "label": "Item #",
                "format": "number",
                "colname": "Item #",
                "default": 1,
                "key": "line_id"
            },
            {
                "label": "Item Name",
                "format": "string",
                "colname": "Item Name",
                "default": 1,
                "key": "name"
            },
            {
                "label": "Quantity (- Refund)",
                "format": "number",
                "colname": "Quantity (- Refund)",
                "default": 1,
                "key": "qty_minus_refund"
            },
            {
                "label": "Item Cost",
                "format": "money",
                "colname": "Item Cost",
                "default": 1,
                "key": "item_price"
            }
        ],
        "order_coupon_fields": [
            {
                "label": "Coupon Code",
                "format": "string",
                "colname": "Coupon Code",
                "default": 1,
                "key": "code"
            },
            {
                "label": "Discount Amount",
                "format": "money",
                "colname": "Discount Amount",
                "default": 1,
                "key": "discount_amount"
            },
            {
                "label": "Discount Amount Tax",
                "format": "money",
                "colname": "Discount Amount Tax",
                "default": 1,
                "key": "discount_amount_tax"
            }
        ],
        "id": 0,
        "post_type": "shop_order",
        "export_rule_field": "date",
        "export_filename": "orders-%y-%m-%d-%h-%i-%s.xlsx",
        "summary_row_title": "Total"
    },
    "profiles": [],
    "cron": [],
    "order-action": []
}
```

Click on the "Export Now" tab. Set the desired date range. In the "Filter By Product" section, populate the "Product Categories" field with the categories that you need to calculate commissions for. Click the "Save Settings" button at the bottom of the screen to save the categories for future use. You will need to change the date ranges each time.

In the "Set up fields to export" section, it should list only 6 fields. Order Date, Category, Item Name, Quantity (- Refund), Item Cost, btcusd. Do not change these or their order.

Click the "Export" button at the bottom and it should generate and download an XLSX file.

From the folder where you saved `commission_calculator.py` launch a Windows Command Prompt and run
```
python commission_calculator.py
```

When promted to select a file, select the XLSX file you downloaded from WooCommerce. It will prompt you for a % to assign to each category. Just type the number. If Bob gets 50% commission, type 50 and ENTER. Do the same for each category. Once all the categories are completed, the script will save a TXT file in the same directory the script file is located in, indicating how many sats is the commission for each category.

